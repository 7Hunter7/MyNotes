<template>
  <AppHeader />
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
    <div>
      <TextareaComponent
        label="Введите значение"
        placeholder="Введите значение"
        :model-value="description"
        @update:model-value="description = $event"
      />
      <p>Описание: {{ description }}</p>
    </div>
    <div>
      <h1>Мои заметки</h1>
      <NotesList />
    </div>
  </main>
</template>

<script setup lang="ts">
import { ref } from 'vue'
import { RouterLink, RouterView } from 'vue-router'
import AppHeader from '@/components/AppHeader.vue'
import ButtonWithText from '@/components/ButtonWithText.vue'
import TextareaComponent from '@/components/TextareaComponent.vue'
import NotesList from '@/components/NotesList.vue'

const description = ref('')
</script>

<style scoped></style>
