<template>
  <p>{{ msg }}</p>
</template>
<script>
import { ref } from 'vue'

export default {
  setup () {
    const msg = ref('blue')
    return {
      msg
    }
  }
}
</script>
<style>
p {
  color: var(--primary)
}
</style>
