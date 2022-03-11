<template>
  <div id="app">
    <div class="menu">
      <DefaultMenu/>
      <transition name="pagina">
      <router-view></router-view>
      </transition>
    </div>
  </div>
</template>

<script>
import DefaultMenu from './components/defaultMenu/DefaultMenu.vue'
export default {
  components: {
    DefaultMenu,
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
  background-color: #202429;
}

body {
  background-color: #202429;
}

.menu {
  display: flex;
  justify-content: right;
}

.pagina-enter, .pagina-leave-active {
  opacity: 0;
}

.pagina-enter-active, .pagina-leave-active {
  transition-delay: 1s;
  transition: all 500ms ease-in-out;
}
</style>
