<template>
    <div class="menu-container">
      <div class="sidebar-header">
        <img class="logo" src="../../assets/alura.jpg"/>
        <span class="title">Alurapic</span>
      </div>
      <DefaultInput @input="filtro = $event.target.value" classe="filtro-sidebar" placeholder=" Filtre pelo título"/>
      <button v-for="(route,index) in routes" class="btn sidebar sidebar-third" @click="redirect(route)">{{nomes[index]}}</button>
    </div>
</template>

<script>
import {routes} from '../../routes';
import DefaultInput from '../shared/defaultInput/DefaultInput.vue'
export default {
  name: 'DefaultMenu',
  components: {
    DefaultInput,
  },
  data () {
    return {
      filtro:'',
      routes,
      nomes: [
        'Home',
        'Cadastro'
      ]
    }
  },
  methods: {
    redirect(value) {
      this.$router.push(value);
    }
  }
}
</script>

<style>
.menu-container {
  min-width: 265px;
  height: 100%;
  position: fixed;
  background-color: blue;
  display: flex;
  flex-direction: column;
  top:0;
  left:0;
  transition: 0.2s ease-in-out;
  z-index: 3;
}
.sidebar-header {
  display: flex;
  justify-content: space-between;
  align-items: center;
}
.logo {
  width: 80px;
  height: 80px;
  align-self: flex-start;
  margin-left: 7px;
}
.title {
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
  font-size: 26px;
  color: #fff;
  font-weight: 700;
  margin-right: 36px;
}

.sidebar {
  margin: 5px;
  width: 93%;
  text-align: center;
  align-items: center;
  justify-content: center;
}
.sidebar-third {
  border-color: #3498db;
  color: #fff;
  box-shadow: 0 0 40px 40px #3498db inset, 0 0 0 0 #3498db;
  -webkit-transition: all 150ms ease-in-out;
  transition: all 150ms ease-in-out;
}
.sidebar-third:hover {
  box-shadow: 0 0 10px 0 #3124e2 inset, 0 0 10px 4px #3124e2;
  background-color: #fff;
  color: #000 !important;
}
</style>
