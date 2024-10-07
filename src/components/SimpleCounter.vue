<script setup lang="ts">
import { ref, onMounted, withDefaults } from 'vue'
import fetchCount from '../services/fetchCount'
import EmittingBtn from './EmittingBtn.vue'

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
const resetCount = () => {
  count.value = 0
}

onMounted(() => {
  fetchCount((initialCount) => {
    count.value = initialCount
  })
})
</script>

<template>
  <p>Count: {{ count }}</p>
  <EmittingBtn @add-count="addCount" @reset-count="resetCount" />
</template>
