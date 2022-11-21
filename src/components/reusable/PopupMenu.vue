<template>
    <div>
        <button class="icon-button round" v-on:mouseover="menuActive(true)" v-on:mouseleave="menuActive(false)">
            <img v-if="isIconButton && isImgIcon" :src="iconImgSrc" />
            <font-awesome-icon v-if="isIconButton && !isImgIcon" :icon="faIcon" :size="faIconSize" />
            <span v-else>{{ displayText }}</span>
        </button>
        <div :class="defineClass">
            <div class="menu-item" v-for="option in options" :key="option.value">
                <button @click="menuItemSelected(option.value)">
                    <img v-if="option.imgSrc" :src="option.imgSrc" :alt="option.label" />
                    <font-awesome-icon v-else-if="option.faIcon" :icon="option.faIcon"
                        :size="!!option.faIconSize ? option.faIconSize : '1x'" />
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
    data() {
        return {
            isOpen: false
        }
    },
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
        defineClass(): String {
            return this.determineAlignment.concat(this.determineHidden);
        },
        determineAlignment(): string {
            if (this.alignment === 'left') {
                return 'menu left';
            }
            return 'menu';
        },
        determineHidden(): string {
            return this.isOpen ? '' : ' hidden';
        }
    },
    methods: {
        menuItemSelected(itemValue: String) {
            this.$emit('menu-item-selected', itemValue);
        },
        menuActive(mouseHover: boolean): void {
            this.isOpen = mouseHover;
        }
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
                width: 30px;
                margin-right: 10px;
            }

            svg {
                margin-right: 10px;
            }

            &:hover {
                background-color: var(--primary-color);
                border-radius: 5px;
                transition: 0.3s;
            }
        }
    }

    &.left {
        transform: translateX(-70%);
    }

    @keyframes hidden {
        0% {
            opacity: 0;
            transform: translateY(-20px);
        }

        100% {
            opacity: 1;
            transform: translateY(0);
        }
    }
}
</style>