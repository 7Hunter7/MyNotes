<template>
  <a class="link" :href="href" :target="target">
    <slot>{{ text }}</slot>
  </a>
</template>

<script setup lang="ts">
import { defineProps } from 'vue'

interface Props {
  href: string
  text?: string
  target?: '_blank' | '_self' | '_parent' | '_top' // Необязательный целевой атрибут
}

const props = defineProps<Props>()
</script>

<style scoped>
.link {
  font-family: var(--font-family);
  font-weight: 700;
  font-size: 1.125rem;
  line-height: 156%;
  color: var(--green-light);
  text-decoration: none;
  cursor: pointer;
  transition: color 0.2s ease;
}
.link:hover {
  color: var(--white);
}
</style>
