<script setup lang="ts">
import { RouterLink, RouterView } from 'vue-router'
import Header from './components/Header.vue';
</script>

<template>
  <div class="container dark-theme">
    <Header />
    <div class="router-container">
      <RouterView />
    </div>
  </div>
</template>

<style>
  @import './assets/style.css';
  @import '../node_modules/typeface-roboto/index.css';
</style>
