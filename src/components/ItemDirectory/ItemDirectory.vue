<template>
  <div>
    <slot></slot>
    <header
      class="folder__title"
      @click="showTree = !showTree"
      tabindex="0"
    >
      {{list.name}}
    </header>
    <ul class="folder__tree"
      v-if="showTree"
    >
      <ListItem
        v-for="subdir in list.contents"
        :key="subdir.name"
        :list="subdir"
      />
    </ul>
  </div>
</template>

<script>

export default {
  name: 'ItemDirectory',
  props: {
    list: {
      type: Object,
      require: true,
    }
  },
  data() {
    return {
      showTree: false
    }
  },
  components: {
    ListItem: () => import('@components/ListItem/ListItem.vue'),
  },
}
</script>

<style scoped>
  .folder__title {
    display: inline-flex;
    color: #777;
    font-weight: bold;
    cursor: pointer;
  }

  .folder__tree {
    margin-left: 10px;
    padding-left: 20px;
    border-left: 1px dashed #ddd;
  }

  .folder__tree li {
    list-style: none;
    color: #888;
    font-size: 17px;
    font-style: italic;
    font-weight: normal;
  }
</style>