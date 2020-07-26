<template>
  <p>{{ msg }}</p>
</template>
<script>
function sleep (ms) {
  return new Promise(resolve => setTimeout(resolve, ms))
}

export default {
  props: ['msg'],
  async setup () {
    await sleep(5000).then(() => console.log('done sleeping'))

    return {
    }
  }
}
</script>
<style scoped>
p {
  color: var(--primary)
}
</style>
