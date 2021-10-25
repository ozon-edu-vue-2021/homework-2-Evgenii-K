<template>
  <div>
    <slot></slot>
    <header
      :class="['title', {
        'link__title': isLink
      }]"
      @click="isSelected"
    >
      {{list.name}}
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
    isLink () {
      return this.properties.type === 'link'
    }
  },
  methods: {
    isSelected() {

    }
  }
}
</script>

<style scoped>
  .title {
    display: inline-flex;
  }
</style>