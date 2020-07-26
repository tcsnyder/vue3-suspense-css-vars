<template>
  <!-- Syncronous components inherit the css variables. works as expected-->
  <h3>Standard Component</h3>
  <SyncComponent />

  <hr>
  <!-- Top level suspense component does not inherit the css variable for #default template or for #fallback template -->
  <h3>Top level Suspense Component</h3>

  <Suspense>
    <template #fallback>
      <p>fallback is not blue...</p>
    </template>
    <template #default>
      <AsyncComponent msg="not blue" />
    </template>
  </Suspense>

  <hr>

  <!-- Wrapping the suspense component in a div fixes the problem since the wrapping div inherits the css variables -->
  <h3>Wrap the Suspense component in a div</h3>
  <div>
    <Suspense>
      <template #fallback>
        <p>fallback is blue...</p>
      </template>
      <template #default>
        <AsyncComponent msg="blue" />
      </template>
    </Suspense>
  </div>
</template>

<script>
import { ref } from 'vue'
import AsyncComponent from './components/AsyncComponent.vue'
import SyncComponent from './components/SyncComponent.vue'

export default {
  name: 'App',
  components: {
    AsyncComponent,
    SyncComponent
  },
  setup () {
    const primary = ref('blue')

    return { primary }
  }
}
</script>
<style vars="{ primary }">
p {
  color: var(--primary)
}
</style>
