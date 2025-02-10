<template>
  <AppHeader />
  <HomeView />
</template>

<script setup lang="ts">
import { ref } from 'vue'
import AppHeader from '@/components/AppHeader.vue'
import HomeView from '@/views/HomeView.vue'

const description = ref('')
</script>

<style scoped></style>
