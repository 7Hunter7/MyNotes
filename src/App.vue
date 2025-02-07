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
      <NoteComponent :note="myNote" :has-text="false" @delete="handleDelete" />
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
import ButtonWithText from '@/components/ButtonWithText.vue'
import TextareaComponent from '@/components/TextareaComponent.vue'
import NoteComponent from '@/components/NoteComponent.vue'
import NotesList from '@/components/NotesList.vue'

const description = ref('')

const myNote = ref({
  id: '123',
  title: 'Моя первая заметка',
  text: 'Текст моей первой заметки.',
})

const handleDelete = (id: string) => {
  alert(`Удалить заметку с id: ${id}`)
  // Здесь будет логика удаления заметки
}
</script>

<style scoped></style>
