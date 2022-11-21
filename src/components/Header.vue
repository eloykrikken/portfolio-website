<template>
    <div class="header-container">
        <img alt="logo" class="header-logo" src="../assets/images/logo.png" />
        <h1>Eloy Krikken</h1>
        <div class="align-right">
            <div class="nav-button">
                <popup-menu 
                    :isIconButton="true"
                    faIcon="fa-solid fa-globe"
                    :options="[{
                        label: 'TestOption1',
                        value: 'test1',
                        faIcon: 'fa-solid fa-globe'
                    },
                    {
                        label: 'TestOption2',
                        value: 'test2',
                    },
                    {
                        label: 'TestOption3',
                        value: 'test3',
                        imgSrc: 'src/assets/images/logo.png'
                    }]"
                    @menu-item-selected="log"
                />
            </div>
            <div class="nav-button">
                <button class="icon-button round-button">
                    <img src="../assets/images/empire.png" />
                </button>
            </div>
        </div>
    </div>
</template>

<script lang="ts">
import PopupMenu from './reusable/PopupMenu.vue'

export default {
    components: { PopupMenu },
    name: 'Header',
    methods: {
        log(clicked: string) {
            console.log(clicked)
        },
    },
}
</script>

<style scoped lang="scss">
.header-container {
    display: flex;
    align-items: center;
}
.header-logo {
    width: 100px;
    padding: 20px;
}

.align-right {
    display: flex;
    margin-left: auto;
    padding: 20px;
}

.nav-button {
    margin-left: 20px;
}
</style>
