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
            <div class="menu-item">
                <span>Placeholder Text</span>
            </div>
            <div class="menu-item">Placeholder Text</div>
            <div class="menu-item">Placeholder Text</div>
        </div>
    </div>
</template>
<script lang="ts">
export default {
    name: 'PopupMenu',
    props: {
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