<template>
  <div id="app">
    <div id="nav container" v-if="isLogin">
      <router-link to="/">Home</router-link> |
      <button @click.prevent="logout">Logout</button>
    </div>
    <router-view/>
  </div>
</template>

<script>
export default {
  name: 'App',
  methods: {
    logout () {
      localStorage.clear()
      this.$store.commit('setLogin', false)
      this.$router.push('/login')
    }
  },
  computed: {
    isLogin: {
      get () {
        return this.$store.state.isLogin
      }
    }
  }
}
</script>
<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
}

#nav {
  padding: 30px;
}

#nav a {
  font-weight: bold;
  color: #2c3e50;
}

#nav a.router-link-exact-active {
  color: #42b983;
}
</style>
