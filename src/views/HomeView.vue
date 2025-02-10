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
  max-width: 120rem;
  padding: 0px 5rem;
  display: flex;
  flex-direction: row;
  align-items: center;
  justify-content: space-between;
  gap: 13.375rem;

  &__container {
    display: flex;
    flex-wrap: nowrap;
    flex-direction: column;
    align-items: flex-start;
    justify-content: center;
    gap: 2.5rem;

    &_title {
      font-weight: 900;
      font-size: 6.5rem;
      line-height: 100%;
    }
    &_description {
      font-weight: 400;
      font-size: 2rem;
      line-height: 150%;
      color: var(--gray);
    }
  }
  &__img {
    width: 100%;
    height: 54rem;
  }
}
</style>
