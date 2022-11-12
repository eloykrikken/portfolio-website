<template>
    <div class="header-container">
        <img alt="logo" class="header-logo" src="../assets/images/logo.png" />
        <h1>Eloy Krikken</h1>
        <popup-menu 
                :isIconButton="true"
                faIcon="fa-solid fa-globe"
                alignment="right"/>
        <div class="align-right">
            <div class="nav-button">
                <popup-menu 
                :isIconButton="true"
                faIcon="fa-solid fa-globe"/>
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
import PopupMenu from './reusable/PopupMenu.vue';

export default {
  components: { PopupMenu },
    name: 'Header'
}
</script>

<style scoped>
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
