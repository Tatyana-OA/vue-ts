<script setup lang="ts">
import { ref, reactive } from 'vue'

interface AppInfo {
  name: string
  slogan: string
}

const count = ref<null | number>(0) // if type iwll be reassigned.
const appInfo: AppInfo = reactive({
  // Specific type assigned
  name: 'Counter',
  slogan: 'An app you can count on'
})

// All is inferred
const addCount = () => {
  if (count.value !== null) {
    count.value++
  }
}

const AddSpecificNumber = (num: number) => {
  if (count.value !== null) {
    count.value += num
  }
}

console.log(count)
</script>

<template>
  <h1>{{ appInfo.name }}</h1>
  <h2>{{ appInfo.slogan }}</h2>
  <p>Count: {{ count }}</p>
  <button @click="addCount">ADD</button>
  <button @click="AddSpecificNumber(3)">ADD 3</button>
</template>
