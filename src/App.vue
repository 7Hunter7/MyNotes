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
        label="Описание"
        placeholder="Введите описание"
        :model-value="description"
        @update:model-value="description = $event"
      />
      <p>Описание: {{ description }}</p>
    </div>
    <div>
      <Note :note="myNote" :has-text="false" @delete="handleDelete" />
    </div>
  </main>
</template>

<script setup lang="ts">
import { ref } from 'vue'
import { RouterLink, RouterView } from 'vue-router'
import ButtonWithText from '@/components/ButtonWithText.vue'
import TextareaComponent from '@/components/TextareaComponent.vue'
import NoteComponent from '@/components/NoteComponent.vue'

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
