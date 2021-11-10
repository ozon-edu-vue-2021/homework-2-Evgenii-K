<template>
  <div id="app">
    <DirectoryTree msg="Directory List"/>
  </div>
</template>

<script>
import DirectoryTree from '@components/DirectoryTree/DirectoryTree.vue'

export default {
  name: 'App',
  components: {
    DirectoryTree
  }
}
</script>

<style>
</style>
