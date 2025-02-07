<template>
  <div class="textarea-wrapper">
    <label v-if="label" :for="id" class="textarea-label">{{ label }}</label>
    <textarea
      :id="id"
      class="textarea"
      :value="modelValue"
      @input="$emit('update:modelValue', ($event.target as HTMLTextAreaElement).value)"
      :placeholder="placeholder"
      :disabled="isDisabled"
      @focus="isFocused = true"
      @blur="isFocused = false"
      :class="{
        'textarea--focused': isFocused,
        'textarea--disabled': isDisabled,
        'textarea--error': hasError,
      }"
    ></textarea>
    <div v-if="errorMessage && hasError" class="textarea-error-message">{{ errorMessage }}</div>
  </div>
</template>

<script setup lang="ts">
import { ref, onMounted } from 'vue'
import { v4 as uuidv4 } from 'uuid'

interface Props {
  id?: string
  label?: string
  modelValue: string
  placeholder?: string
  isDisabled?: boolean
  errorMessage?: string
  hasError?: boolean
  autoResize?: boolean
}

const props = defineProps<Props>({
  id: {
    type: String,
    default: () => uuidv4(),
  },
  label: {
    type: String,
    default: '',
  },
  modelValue: {
    type: String,
    required: true,
  },
  placeholder: {
    type: String,
    default: '',
  },
  isDisabled: {
    type: Boolean,
    default: false,
  },
  errorMessage: {
    type: String,
    default: '',
  },
  hasError: {
    type: Boolean,
    default: false,
  },
  autoResize: {
    type: Boolean,
    default: true,
  },
})

const emit = defineEmits(['update:modelValue'])
const isFocused = ref(false)
const textarea = ref<HTMLTextAreaElement | null>(null)

onMounted(() => {
  if (props.autoResize && textarea.value) {
    adjustHeight()
  }
})

const adjustHeight = () => {
  if (textarea.value) {
    textarea.value.style.height = 'auto'
    textarea.value.style.height = `${textarea.value.scrollHeight}px`
  }
}
</script>

<style scoped lang="scss">
.textarea-wrapper {
  display: flex;
  flex-direction: column;
  margin-bottom: 1rem;
  font-family: var(--font-family);
  font-weight: 400;
  font-size: 18px;
  line-height: 156%;
  .textarea-label {
    margin-bottom: 0.5rem;
    color: var(--gray);
  }
  .textarea {
    border: 2px solid var(--white);
    border-radius: 2.25rem;
    padding: 1rem;
    width: 42.375rem;
    height: 17.5rem;
    color: var(--dark);
    transition: border-color 0.3s ease;
    resize: vertical;
    overflow: hidden;
    &:hover {
      border-color: var(--green-light);
    }
    &:focus {
      border-color: var(--green-light);
      outline: none;
    }
    &--focused {
      border-color: var(--green-light);
    }
    &--disabled {
      cursor: not-allowed;
    }
    &--error {
      border-color: #dc3545;
      cursor: not-allowed;
    }
  }
  .textarea-error-message {
    margin: 0.5rem 1.5rem;
    color: #ff7461;
  }
}
</style>
