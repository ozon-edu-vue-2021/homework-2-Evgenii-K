<template>
  <div>
    <slot></slot>
    <!-- <icon-folder class="icon"/> -->
    <header
      :class="['title', {
        'folder__title': isFolder
      }]"
      @click="showTree = !showTree"
    >
      {{list.name}}
    </header>
    <ul class="folder_tree"
      v-if="isFolder && showTree"
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
// import IconFolder from '@components/Icons/IconFolder.vue'

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
    // IconFolder
  },
  computed: {
    isFolder () {
      return this.list.contents && this.list.contents.length > 0
    }
  }
}
</script>

<style scoped>
  .item {
    display: inline-flex;
  }
  .title {
    display: inline-flex;
  }

  .folder__title {
    color: #777;
    font-weight: bold;
    cursor: pointer;
  }

  .folder_tree {
    margin-left: 10px;
    padding-left: 20px;
    border-left: 1px dashed #ddd;
  }

  .folder_tree li {
    list-style: none;
    color: #888;
    font-size: 17px;
    font-style: italic;
    font-weight: normal;
  }

  .icon {
    margin-right: 10px;
    content: "";
    height: 16px;
    vertical-align: middle;
    width: 16px;
  }
</style>