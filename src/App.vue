<template>
  <div id="app">
    <MainMenu />
    <router-view></router-view>
  </div>
</template>

<script>
import MainMenu from './components/main-menu'
import { retrieveUser } from './firebase'
import { mapMutations } from 'vuex'

export default {
  name: 'app',
  components: {
    MainMenu
  },
  methods: {
    ...mapMutations(['setUser'])
  },
  created() {
    retrieveUser().then(this.setUser)
  }
}
</script>

<style>
#app {
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
