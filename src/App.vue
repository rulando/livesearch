<template>
  <div id="app">
    <filter-user :users="users"></filter-user>
  </div>
</template>

<script>
import axios from 'axios'
import FilterUser from './components/FilterUser'

export default {
  name: 'App',
  components: {
    FilterUser
  },
  data () {
    return {
      users: []
    }
  },
  created () {
    axios.get('https://jsonplaceholder.typicode.com/users')
      .then((response) => {
        this.users = response.data
      })
  }
}
</script>

<style>
#app {
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
