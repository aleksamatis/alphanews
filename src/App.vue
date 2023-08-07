<script setup>
import { RouterView } from 'vue-router'
import AppHeader from './components/AppHeader.vue'
import NewsFooter from './components/NewsFooter.vue'
</script>

<template>
  <AppHeader />
  <RouterView />
  <NewsFooter />
</template>

<style scoped></style>
