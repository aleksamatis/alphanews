<script setup>
import {computed} from 'vue';

import { defineProps } from 'vue'
import moment from 'moment'

const props = defineProps(['item'])

const date = computed(() => {
  return moment.unix(props.item.date)
})

const year = computed(() => {
  return date.value.year()
})

const month = computed(() => {
  return date.value.format("MMMM")
})

const dayofMonth = computed(() => {
  return date.value.date()
})
</script>
<template> 
  <div class="news-item">
    <img :src="item.image" v-if="item.image" />
    <div class="news-item-content">
      <div class="general-date">
        <div class="news-item-day">{{ dayofMonth }}</div>
        <div class="news-item-month-year">
          <div>{{ month }}</div>
          <div>{{ year }}</div>
        </div>
      </div>
      <div class="item-title">{{ item.name }}</div>
      <div>{{ item.previewText }}</div>
      <div class="news-items-tags">
        <div class="news-item-tag">{{ item.type.value }}</div>
      </div>
    </div>
  </div>
</template>

<style scoped>
.news-item {
  border-radius: var(--radius-m, 16px);
  border: 1px solid var(--color-brend-primary, #0f62fe);
  overflow: hidden;
  display: flex;
  flex-direction: column;
}
.news-item img {
  width: 100%;
}

.news-item-content {
  padding: 32px;
  display: flex;
  flex-direction: column;
  flex-grow: 1;
}

.news-items-tags {
    margin-top: 16px;
    flex: 1;
    display: flex;
    align-items: flex-end;
}

.news-item-tag {
    display: inline;
    padding: 4px 16px;
    border-radius: var(--radius-full, 360px);
    background: var(--bg-bg-5, #F0F6FE);
    margin-right: 2px;
}
.news-item-tag:last-child {
    margin-right: 0;
}
.news-item-day {
  color: #A1A7B5;
  font-weight: 400;
  font-size: 36px;
  line-height: 100%; /* 36px */
}
.general-date {
  display: flex;
  align-items: flex-end;
  gap: 4px;
}
.news-item-month-year {
  color: #A1A7B5;
  font-weight: 700;
  line-height: 110%; /* 16.5px */
  font-size: 15px;
  letter-spacing: -0.15px;
}
.item-title {
  font-weight: 400;
  font-size: 22px;
  line-height: 26.4px;
  color:#0C5BEF;
  padding-top: 16px;
  padding-bottom: 16px;
}
</style>
