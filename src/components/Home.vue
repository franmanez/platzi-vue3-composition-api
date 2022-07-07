<template>
  <div>Composition API</div>
</template>

<script>

import { onMounted } from 'vue'

export default {
  // eslint-disable-next-line vue/multi-word-component-names
  name: 'Home',
  setup (props, ctx) {
    onMounted(() => {
      console.log('mounted')
    })
  }
}
</script>
