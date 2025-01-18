<script setup lang="ts">
import AppFooter from './components/organisms/AppFooter.vue'
import AppHeader from './components/organisms/AppHeader.vue'
</script>

<template>
  <AppHeader></AppHeader>

  <main>
    <RouterView />
  </main>

  <AppFooter></AppFooter>
</template>

<style lang="css" scoped></style>
