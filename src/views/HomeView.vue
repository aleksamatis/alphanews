<script setup>
import NewsHeader from '@/components/NewsHeader.vue'
import NewsItems from '@/components/NewsItems.vue'
</script>

<template>
  <main>
    <NewsHeader class="news-header" />
    <NewsItems />
  </main>
</template>

<style scoped>
.news-header {
  margin-bottom: 64px;
}
</style>
