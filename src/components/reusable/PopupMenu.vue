<template>
    <div>
        <button class="icon-button round">
            <img v-if="isIconButton && isImgIcon" :src="iconImgSrc" />
            <font-awesome-icon 
                        v-if="isIconButton && !isImgIcon"
                        :icon="faIcon" 
                        :size="faIconSize" 
                    />
            <span v-else>{{ displayText }}</span>
        </button>
        <div :class="determineAlignment">
            <div class="menu-item" v-for="option in options" :key="option.value">
                <button @click="menuItemSelected(option.value)">
                    <img v-if="option.imgSrc" :src="iconImgSrc" :alt="option.label"/>
                    <font-awesome-icon 
                        v-else-if="option.faIcon"
                        :icon="option.faIcon"
                        :size="!!option.faIconSize ? option.faIconSize : '1x'" 
                    />
                    <span>{{ option.label }}</span>
                </button>
            </div>
        </div>
    </div>
</template>
<script lang="ts">
import type { PropType } from '@vue/runtime-core'
import type MenuOption from '../../assets/interfaces/menuOption'

export default {
    name: 'PopupMenu',
    props: {
        options: {
            type: Array as PropType<Array<MenuOption>>,
            required: true,
        },
        alignment: {
            type: String,
            default: 'left',
        },
        isIconButton: {
            type: Boolean,
            default: false,
        },
        isImgIcon: {
            type: Boolean,
            default: false,
        },
        iconImgSrc: String,

        faIcon: String,
        faIconSize: {
            type: String,
            default: '2x',
        },

        displayText: String,
    },
    computed: {
        determineAlignment(): String {
            if (this.alignment === 'left') {
                return 'menu left'
            }
            return 'menu'
        },
    },
    methods: {
        menuItemSelected(itemValue: String) {
            this.$emit('menu-item-selected', itemValue)
        },
    },
}
</script>
<style scoped lang="scss">
.menu {
    position: absolute;

    margin-top: 10px;

    background-color: var(--background-secondary-color);
    border-radius: 5px;
    z-index: 1001;

    &.left {
        transform: translateX(-70%);

        .menu-item {
            height: 50px;

            display: flex;

            button {
                width: 100%;
                height: 100%;
                align-items: center;
                cursor: pointer;
                display: flex;
                background: none;
                border: inherit;
                color: inherit;
                font-size: 20px;

                img {
                    margin-right: 10px;
                }
                svg {
                    margin-right: 10px;
                }

                &:hover {
                    background-color: var(--secondary-color);
                    border-radius: 5px;
                }
            }
        }
    }
}
</style>