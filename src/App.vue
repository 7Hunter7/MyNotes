<template>
  <header>
    <div class="wrapper">
      <nav>
        <RouterLink to="/">Home</RouterLink>
      </nav>
    </div>
  </header>

  <RouterView />
  <main>
    <ButtonWithText text="Вход" />
  </main>
</template>

<script setup lang="ts">
import { RouterLink, RouterView } from 'vue-router'
import ButtonWithText from '@/components/ButtonWithText.vue'
</script>

<style scoped></style>
