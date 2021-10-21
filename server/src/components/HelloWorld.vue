<template>
  <div class="hello">
    <h1>{{ msg }}</h1>
    <h2>Essential Links</h2>
    <ul v-for="item in items" :key="item.title">
      <li>
        {{ item.title }} : {{ item.description }}
      </li>
    </ul>
    <div>{{ postsData }}</div>
    <button class="btn btn-primary">bootstrap-btn</button>
    <b-button variant="primary">bootstrap-vue-btn</b-button>
  </div>
</template>

<script>
import testJson from '../assets/test'
export default {
  name: 'HelloWorld',
  icons: {
    iconfont: 'mdi' // 追加
  },
  data () {
    return {
      msg: 'Welcome to invoice App',
      items: testJson.sampleData,
      postsData: '',
      fetchUrl: process.env.FETCH_URL
    }
  },
  // created () {
  // },
  // compute: {
  // },
  created: async function () {
    const response = await fetch(this.fetchUrl)
    this.postsData = await response.json()
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
h1, h2 {
  font-weight: normal;
}
ul {
  list-style-type: none;
  padding: 0;
}
li {
  display: inline-block;
  margin: 0 10px;
}
a {
  color: #42b983;
}
</style>
