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
interface Props {
  text?: string
  hasIcon?: boolean
  hasText?: boolean
  isRound?: boolean
  isDisabled?: boolean
}

const props = withDefaults(defineProps<Props>(), {
  hasIcon: false,
  hasText: false,
})
const emit = defineEmits(['click'])
</script>

<style scoped lang="scss">
.button {
  display: inline-flex;
  align-items: center;
  justify-content: center;
  padding: 1.5rem 1.5rem;
  border: none;
  border-radius: 2rem;
  cursor: pointer;
  transition: background-color 0.2s ease;
  color: var(--white);
  background-color: var(--green-light);
  &:hover {
    background-color: var(--green-middle);
  }
  &:active {
    background-color: var(--green-dark);
  }
  &--disabled {
    background-color: var(--gray);
    cursor: not-allowed;
  }

  &--icon-text {
    display: flex;
    flex-direction: row;
    align-items: center;
    justify-content: center;
    gap: 0.75rem;
  }
  &--round {
    border-radius: 50%;
    width: 3.5rem;
    height: 3.5rem;
    padding: 0;
  }
  &__icon {
    margin-right: 0.5rem;
    display: inline-flex;
  }
  &__text {
    font-family: var(--font-family);
    font-weight: 500;
    font-size: 1.25rem;
    line-height: 160%;
    color: var(--white);
  }
}
</style>
