<template>
    <div class="header-container">
        <img alt="logo" class="header-logo" src="../assets/images/logo.png" />
        <h1>Eloy Krikken</h1>
        
        <div class="align-right">
            <div class="nav-button">
                <button class="icon-button round-button">
                    <font-awesome-icon 
                        icon="fa-solid fa-globe" 
                        size="2x" 
                    />
                </button>
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
export default {
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
