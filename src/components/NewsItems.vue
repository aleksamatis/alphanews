<script setup>
import {onMounted, ref, computed} from 'vue';

import NewsItem from './NewsItem.vue'

const items = ref([]);
const nav = ref();

async function loadNews() {
  const page = nav.value ? nav.value.current + 1 : ""
  const result = await fetch(`//flems.github.io/test/api/news/${page}`, { credentials: "omit"});
  const jsonData = await result.json()
  nav.value = jsonData.nav

  items.value = items.value.concat(jsonData.items)
}

const hasMoreNews = computed(() => {
  return nav.value && nav.value.current < nav.value.total;
})


onMounted(async () => {
  await loadNews()
})

</script>
<template>
  <section class="news-items-section section">
    <NewsItem :item="item" v-for="item in items" :key="item.id" />
  </section>
  <button v-if="hasMoreNews" class="news-button" @click="loadNews">Загрузить ещё</button>
</template>

<style scoped>
section {
  margin-bottom: 72px;
}
.news-items-section {
  display: grid;
  grid-template-columns: 1fr 1fr 1fr;
  column-gap: 48px;
  row-gap: 64px;
}

@media screen and (max-width: 768px) {
  .news-items-section {
  grid-template-columns: 1fr 1fr;
}
}

@media screen and (max-width: 500px) {
  .news-items-section {
  grid-template-columns: 1fr;
}
}
.news-items-section > div {
  height: 100%;
}

.news-button {
  width: 203px;
  height: 56px;
  display: block;
  color: #002DBF;
  border: 1px solid #002DBF;
  border-radius: 8px;
  font-weight: 600;
  font-size: 20px;
  line-height: 24px;
  letter-spacing: -1%;
  cursor: pointer;
  text-align: center;
  background: transparent;
  margin: 0 auto;
  margin-bottom: 72px;
}
</style>
