<template>
  <div>
    <h1>{{ msg }}</h1>
    <div class="wrapper">
      <h2>{{ `./${fetchDirList.name}` }}</h2>
      <ul>
          <ListItem
            v-for="item in fetchDirList.contents"
            :key="item.name"
            :list="item"
          />
      </ul>
    </div>
  </div>
</template>

<script>
import ListItem from './ListItem.vue'
import jsonFile from '../../public/static/node_modules.json'

export default {
  name: 'HelloWorld',
  props: {
    msg: String
  },
  data() {
    return {
      fetchDirList: {}
    }
  },
  components: {
    ListItem
  },
  mounted() {
    this.getFolders();
  },
  methods: {
    getFolders() {
      new Promise(response => {
        response(JSON.stringify(jsonFile))
      })
      .then(jsonData => this.fetchDirList = JSON.parse(jsonData))
      .catch(err => console.log(err))
    }
  }
}
</script>

<style scoped>
  body {
    background: #eee;
    font-family: "times new roman", serif;
    line-height: 30px;
  }

  h1 {
    color: #aaa;
    font-size: 30px;
    line-height: 40px;
    font-style: italic;
    font-weight: 200;
    margin: 40px;
    text-align: center;
    text-shadow: 1px 1px 1px rgba(255, 255, 255, 0.7);
  }

  h2 {
    color: #aaa;
    font-size: 20px;
    line-height: 20px;
    font-style: italic;
    font-weight: 200;
    margin: 20px;
    margin-left: 60px;
    text-align: left;
    text-shadow: 1px 1px 1px rgba(255, 255, 255, 0.7);
  }

  .wrapper {
    background: #fff;
    border-radius: 2px;
    box-shadow: 0 0 50px rgba(0, 0, 0, 0.1);
    margin: 40px auto;
    padding: 5%;
    max-width: 800px;
  }
</style>
