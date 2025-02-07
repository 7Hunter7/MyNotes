<template>
  <div class="input-wrapper">
    <label v-if="label" :for="id" class="input-label">{{ label }}</label>
    <div class="input-container">
      <input
        :id="id"
        class="input"
        :type="inputType"
        :value="modelValue"
        @input="$emit('update:modelValue', ($event.target as HTMLInputElement).value)"
        :placeholder="placeholder"
        :disabled="isDisabled"
        @focus="isFocused = true"
        @blur="isFocused = false"
        :class="{
          'input--focused': isFocused,
          'input--disabled': isDisabled,
          'input--error': hasError,
        }"
      />
      <button
        v-if="type === 'password'"
        type="button"
        class="password-toggle"
        @click="togglePasswordVisibility"
      >
        <svg
          width="18"
          height="14"
          viewBox="0 0 18 14"
          fill="none"
          xmlns="http://www.w3.org/2000/svg"
        >
          <path
            d="M17 7C17 8.15478 16.2206 9.64926 14.7228 10.9006C13.2537 12.128 11.2258 13 9 13C6.77424 13 4.7463 12.128 3.27718 10.9006C1.77936 9.64926 1 8.15478 1 7C1 5.84522 1.77936 4.35074 3.27718 3.09941C4.7463 1.87204 6.77424 1 9 1C11.2258 1 13.2537 1.87204 14.7228 3.09941C16.2206 4.35074 17 5.84522 17 7Z"
            stroke="#B1C909"
            stroke-width="2"
          />
          <circle cx="9" cy="7" r="3" stroke="#B1C909" stroke-width="2" />
        </svg>
      </button>
    </div>
    <div v-if="errorMessage && hasError" class="input-error-message">{{ errorMessage }}</div>
  </div>
</template>

<script setup lang="ts">
import { ref } from 'vue'
import { v4 as uuidv4 } from 'uuid'

interface Props {
  id?: string
  label?: string
  type?: 'text' | 'email' | 'password'
  modelValue: string
  placeholder?: string
  isDisabled?: boolean
  errorMessage?: string
  hasError?: boolean
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
  type: {
    type: String,
    default: 'text' as 'text' | 'email' | 'password',
    validator: (value: string) => {
      return ['text', 'email', 'password'].includes(value)
    },
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
})

const emit = defineEmits(['update:modelValue'])
const isFocused = ref(false)
const passwordVisible = ref(false)

const inputType = ref(props.type)
const togglePasswordVisibility = () => {
  passwordVisible.value = !passwordVisible.value
  inputType.value = passwordVisible.value ? 'text' : 'password'
}
</script>

<style scoped lang="scss">
.input-wrapper {
  display: flex;
  flex-direction: column;
  max-width: 45rem;
  margin-bottom: 1rem;
  padding: 1.25rem;
  font-family: var(--font-family);
  font-weight: 400;
  font-size: 1.125rem;
  line-height: 156%;
}
.input-label {
  color: var(--gray);
  margin-bottom: 0.5rem;
}
.input-container {
  position: relative;
  display: flex;
  align-items: center;
  .input {
    width: 100%;
    border-radius: 2.25rem;
    padding: 1.4rem 3.625rem 1.4rem 1.75rem;
    background-color: var(--white);
    border: 2px solid var(--white);
    color: var(--dark);
    transition: border-color 0.3s ease;
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
      border-color: #ff7461;
      cursor: not-allowed;
    }
  }
  .password-toggle {
    position: absolute;
    right: 0;
    top: 50%;
    transform: translateY(-50%);
    background: none;
    border: none;
    padding: 0;
    margin-right: 1.75rem;
    cursor: pointer;
    outline: none;
    svg {
      display: block;
    }
  }
}
.input-error-message {
  margin: 0.5rem 1.5rem;
  color: #ff7461;
}
</style>
