<template>
  <div class="notes-list">
    <NoteComponent :note="notes[0]" :has-text="true" @delete="handleDelete" />
    <!-- цикл v-for для отображения всех заметок -->
  </div>
</template>

<script setup lang="ts">
import { ref } from 'vue'
import NoteComponent from './NoteComponent.vue'

interface NoteType {
  id: string
  title: string
  text: string
}

const notes = ref<NoteType[]>([
  {
    id: '1',
    title: 'Заголовок',
    text: 'А также явные признаки победы институционализации могут быть объединены в целые кластеры себе подобных.',
  },
])

const handleDelete = (id: string) => {
  alert(`Удалить заметку с id: ${id}`)
  // Здесь будет логика удаления заметки из массива notes
}
</script>

<style scoped lang="scss">
.notes-list {
  padding: 1rem;
}
</style>
