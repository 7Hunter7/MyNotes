<template>
  <div class="note">
    <h3 class="note__title">{{ note.title }}</h3>
    <p class="note__text">{{ note.text }}</p>
    <div class="note__actions">
      <ButtonComponent
        :isRound="false"
        :hasIcon="true"
        :hasText="true"
        text="Удалить"
        @click="emit('delete', note.id)"
      >
        <template #icon>
          <!-- Иконка крестика (удалить) -->
          <svg
            width="18"
            height="18"
            viewBox="0 0 18 18"
            fill="none"
            xmlns="http://www.w3.org/2000/svg"
          >
            <path d="M1 1L17 17M17 1L1 17" stroke="white" stroke-width="2" stroke-linecap="round" />
          </svg>
        </template>
      </ButtonComponent>
    </div>
  </div>
</template>

<script setup lang="ts">
import { computed } from 'vue'
import ButtonComponent from './ButtonComponent.vue'

interface Props {
  note: {
    id: string
    title: string
    text: string
  }
  hasText?: boolean
}

const props = defineProps<Props>()
const emit = defineEmits(['delete'])
const hasText = computed(() => props.hasText !== false)
</script>

<style scoped lang="scss">
.note {
  margin: 1.25rem;
  max-width: 30rem;
  min-height: 20rem;
  display: flex;
  flex-direction: column;
  align-items: flex-start;
  justify-content: flex-start;
  position: relative;
  padding: 1.25rem 1.75rem;
  border-radius: 0.75rem;
  background-color: var(--green-light);
  border-bottom: 1px solid var(--green-middle);
  box-shadow: 0 15px 15px -10px rgba(0, 0, 0, 0.4);
  transition: all 0.3s ease;

  &:hover {
    box-shadow: 0 3px 6px rgba(0, 0, 0, 0.16);
  }
  &__title {
    font-family: var(--font-family);
    font-weight: 600;
    font-size: 1.5rem;
    line-height: 133%;
    color: var(--white);
    margin-bottom: 1.25rem;
  }
  &__text {
    margin-top: 1.25rem;
    font-family: var(--font-family);
    font-weight: 500;
    font-size: 1.25rem;
    line-height: 160%;
    color: var(--white);
    margin-bottom: 0rem;
  }
  &__actions {
    position: absolute;
    bottom: 0.5rem;
    right: 0.5rem;
  }
}
</style>
