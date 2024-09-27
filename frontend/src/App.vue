<template>
  <main>
    <SideBar ref="SideBar"></SideBar>
    <div class="placeholder"></div>
    <Chat></Chat>
    <div class="placeholder"></div>
  </main>
</template>

<script setup lang="ts">
import SideBar from './components/SideBar.vue';
import Chat from './components/Chat.vue'
</script>

<style>
html, body {
  margin: 0;
  padding: 0;
  height: 100%;
}

main {
  height: 100vh;
  display: flex;
  font-family: Verdana, sans-serif;
}

.placeholder {
  width: 20%;
}
</style>