<template>
  <main class="main">
    <div class="main__container">
      <h1 class="main__container_title">Мои заметки</h1>
      <p class="main__container_description">Не забывай о важном, храни его в облаке.</p>
    </div>
    <img class="main__img" :src="Notes" alt="Notes" />
  </main>
</template>

<script setup lang="ts">
import Notes from '/Notes.png'
</script>

<style scoped lang="scss">
.main {
  display: flex;
  flex-direction: row;
  align-items: center;
  justify-content: space-between;

  &__container {
    display: flex;
    flex-wrap: nowrap;
    flex-direction: column;
    align-items: flex-start;
    justify-content: center;
    &_title {
      max-width: 30.5rem;
      font-weight: 900;
      font-size: 6.5rem;
      line-height: 100%;
      margin-bottom: 2.5rem;
    }
    &_description {
      margin-top: 0;
      max-width: 24rem;
      font-weight: 400;
      font-size: 2rem;
      line-height: 150%;
      color: var(--gray);
    }
  }
  &__img {
    display: block;
    width: auto;
    height: 54rem;
  }
}

@media (min-width: 1366px) {
  .main {
  }
}
@media (min-width: 768px) {
  .main {
  }
}
@media (min-width: 360px) {
  .main {
  }
}
</style>
