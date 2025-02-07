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
    <TextareaComponent
      label="Описание"
      placeholder="Введите описание"
      :model-value="description"
      @update:model-value="description = $event"
    />
    <p>Описание: {{ description }}</p>
  </main>
</template>

<script setup lang="ts">
import { ref } from 'vue'
import { RouterLink, RouterView } from 'vue-router'
import ButtonWithText from '@/components/ButtonWithText.vue'
import TextareaComponent from '@/components/TextareaComponent.vue'

const description = ref('')
</script>

<style scoped></style>
