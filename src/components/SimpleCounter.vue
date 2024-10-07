<script setup lang="ts">
import { ref, onMounted, withDefaults } from 'vue'
import fetchCount from '../services/fetchCount'

interface Props {
  limit: number
  alertMessage?: string
}

const props = withDefaults(defineProps<Props>(), {
  alertMessage: 'AAAAAAAA'
})

const count = ref<null | number>(null) // if type iwll be reassigned.

const addCount = () => {
  if (count.value !== null) {
    if (count.value <= props.limit) {
      count.value++
    } else {
      alert(props.alertMessage)
    }
  }
}

const AddSpecificNumber = (num: number) => {
  if (count.value !== null) {
    if (count.value <= props.limit) {
      count.value += num
    } else {
      alert(props.alertMessage)
    }
  }
}

onMounted(() => {
  fetchCount((initialCount) => {
    count.value = initialCount
  })
})
</script>

<template>
  <p>Count: {{ count }}</p>
  <button @click="addCount">ADD</button>
  <button @click="AddSpecificNumber(3)">ADD 3</button>
</template>
