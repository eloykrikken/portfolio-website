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
            <!-- <div class="menu-item">
                <span>Placeholder Text</span>
            </div>
            <div class="menu-item">Placeholder Text</div>
            <div class="menu-item">Placeholder Text</div> -->
            <div class="menu-item" v-for="option in options" :key="option.value">
                <img v-if="option.imgSrc" :src="iconImgSrc" :alt="option.label"/>
                <font-awesome-icon 
                    v-else-if="option.faIcon"
                    :icon="option.faIcon"
                    :size="!!option.faIconSize ? option.faIconSize : '1x'" 
                />
                <button @click="menuItemSelected(option.value)">{{ option.label }}</button>
            </div>
        </div>
    </div>
</template>
<script lang="ts">
import type { PropType } from '@vue/runtime-core';
import type MenuOption from '../../assets/interfaces/menuOption';

export default {
    name: 'PopupMenu',
    props: {
        options: {
            type: Array as PropType<Array<MenuOption>>,
            required: true
        },
        alignment: {
            type: String,
            default: 'left'
        },
        isIconButton: {
            type: Boolean,
            default: false
        },
        isImgIcon: {
            type: Boolean,
            default: false,
        },
        iconImgSrc: String,

        faIcon: String,
        faIconSize: {
            type: String,
            default: '2x'
        },

        displayText: String
    },
    computed: {
        determineAlignment(): String {
            if(this.alignment === 'left') {
                return 'menu left'
            }
            return 'menu'
        }
    },
    methods: {
        menuItemSelected(itemValue: String) {
            this.$emit('menu-item-selected', itemValue);
        }
    }
}
</script>
<style scoped>
    @import '../../assets/style.css';

    .menu {
        position: absolute;

        margin-top: 10px;

        background-color: var(--background-secondary-color);
        border-radius: 5px;
        z-index: 1001;

    }

    .menu.left {
        transform: translateX(-80%);
    }

    .menu-item {
        width: 200px;
        height: 50px;
        padding: 0 10px 0 10px;

        display: flex;
        align-items: center;
    }
</style>