<template>
  <li>
    <item-directory
      v-if="isFolder"
      :list="list"
    >
      <icon-folder class="icon"/>
    </item-directory>
    <item-file
      v-else-if="!isFolder"
      :properties="list"
    >
      <template v-slot:file>
        <icon-file class="icon"/>
      </template>
      <template v-slot:link>
        <icon-link class="icon"/>
      </template>
    </item-file>
  </li>
</template>

<script>
import IconFolder from '@components/Icons/IconFolder.vue'
import IconFile from '@components/Icons/IconFile.vue'
import IconLink from '@components/Icons/IconLink'
import ItemDirectory from '@components/ItemDirectory/ItemDirectory.vue'
import ItemFile from '@components/ItemFile/ItemFile.vue'

export default {
  name: 'ListItem',
  props: {
    list: {
      type: Object,
      require: true,
    }
  },
  components: {
    IconFolder,
    IconFile,
    IconLink,
    ItemDirectory,
    ItemFile
  },
  computed: {
    isFolder () {
      return this.list.type === 'directory'
    },
  }
}
</script>

<style scoped>
  li {
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