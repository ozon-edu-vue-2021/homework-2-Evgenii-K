<template>
  <div>
    <slot 
      :name="isFile ? 'file' : 'link'"
    >
    </slot>
    <header
      tabindex="0"
      :class="headerClasses"
      v-click-inside="selectedHandler"
      v-click-outside="unselectedHandler"
    >
      {{properties.name}}
    </header>
  </div>
</template>

<script>
import clickInside from '@utils/directives/clickInside.js'
import clickOutside from '@utils/directives/clickOutside.js'

export default {
  name: 'ItemFile',
  props: {
    properties: {
      type: Object,
      require: true,
    }
  },
  data() {
    return {
      selected: false
    }
  },
  computed: {
    isFile () {
      return this.properties.type === 'file'
    },    
    headerClasses() {
      return ['title', {
        'selected__title': this.selected
      }]
    }
  },
  directives: {
    clickInside,
    clickOutside
  },
  methods: {
    selectedHandler() {
      this.selected = true
    },
    unselectedHandler() {
      this.selected = false
    },
  },
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