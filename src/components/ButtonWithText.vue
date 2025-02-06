<template>
  <button
    class="button"
    :class="{
      'button--icon-text': hasIcon && hasText,
      'button--round': isRound,
      'button--disabled': isDisabled,
    }"
    :disabled="isDisabled"
    @click="$emit('click')"
  >
    <span v-if="hasIcon" class="button__icon">
      <slot name="icon"></slot>
    </span>
    <span v-if="hasText" class="button__text">
      {{ text }}
    </span>
  </button>
</template>

<script setup lang="ts">
import { defineProps, defineEmits } from 'vue'

interface Props {
  text?: string
  hasIcon?: boolean
  hasText?: boolean
  isRound?: boolean
  isDisabled?: boolean
}

const props = defineProps<Props>({
  text: {
    type: String,
    default: '',
  },
  hasIcon: {
    type: Boolean,
    default: false,
  },
  hasText: {
    type: Boolean,
    default: true,
  },
  isRound: {
    type: Boolean,
    default: false,
  },
  isDisabled: {
    type: Boolean,
    default: false,
  },
})

const emit = defineEmits(['click'])
</script>

<style scoped>
.button {
  display: inline-flex;
  align-items: center;
  justify-content: center;
  padding: 0 1.5rem;
  border: none;
  border-radius: 2rem;
  font-size: 1.25rem;
  cursor: pointer;
  transition: background-color 0.2s ease;
  color: var(--white);
  background-color: var(--green-light);
}
.button:hover {
  background-color: var(--green-middle);
}
.button:active {
  background-color: var(--green-dark);
}
.button--disabled {
  background-color: var(--gray);
  cursor: not-allowed;
}

.button--icon-text {
  display: flex;
  flex-direction: row;
  align-items: center;
  justify-content: center;
  gap: 0.75rem;
}
.button--round {
  border-radius: 50%;
  width: 3.5rem;
  height: 3.5rem;
  padding: 0;
}
.button__icon {
  margin-right: 0.5rem;
  display: inline-flex;
}
</style>
