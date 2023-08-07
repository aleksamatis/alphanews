<template>
  <section class="news-section">
    <div class="section">
      <h1>Новости</h1>
    </div>
  </section>
</template>

<style scoped>
.news-section {
  background: url('../assets/images/news-bg.png') no-repeat;
  background-size: cover;
  height: 320px;
  display: flex;
  align-items: flex-end;
  padding: 48px 0;
}

.news-section > div {
  width: 100%;
}

.news-section h1 {
  color: var(--grey-color-black-90, #17171a);
  /* 4XL/desktop bold */
  font-size: 40px;
  font-weight: 700;
  line-height: 120%; /* 48px */
  letter-spacing: -0.4px;
}
</style>
