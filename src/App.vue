<script setup lang="ts">
import { reactive } from 'vue'
import SimpleCounter from './components/SimpleCounter.vue'

interface AppInfo {
  name: string
  slogan: string
}

const appInfo: AppInfo = reactive({
  // Specific type assigned
  name: 'Counter',
  slogan: 'An app you can count on'
})

// All is inferred
</script>

<template>
  <h1>{{ appInfo.name }}</h1>
  <h2>{{ appInfo.slogan }}</h2>
  <SimpleCounter :limit="10" />
</template>
