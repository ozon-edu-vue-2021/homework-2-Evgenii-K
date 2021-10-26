<template>
  <div>
    <slot 
      v-if="isFile"
      name="file"
    >
    </slot>
    <slot 
      v-if="!isFile"
      name="link"
    >
    </slot>
    <header
      class="title"
    >
      {{properties.name}}
    </header>
  </div>
</template>

<script>
export default {
  name: 'ItemFile',
  props: {
    properties: {
      type: Object,
      require: true,
    }
  },
  computed: {
    isFile () {
      return this.properties.type === 'file'
    }
  }
}
</script>

<style scoped>
  .title {
    display: inline-flex;
    border: 1px solid transparent;
    cursor: default;
  }

  .selected__title {
    border: 1px solid red;
  }
</style>