<template>
  <div class="view-container">
    <h1 class="welcome">{{ welcome }} à {{ title }}, {{ name }}</h1>
    <div class="header">
      <DefaultInput @input="filtro = $event.target.value" placeholder=" Filtre pelo título"/>
      <DefaultButton @click="redirect()">Cadastro</DefaultButton>
    </div>
    <ul class="imageDisp">
        <li v-for="img in filterPhotos">
          <div class="imageWrapper">
            <img  class="dogImage" :src="img.url"  @click="downloadFile(img.url)" :alt="img.titulo">
            <a :href="img.url"></a>
            <span class="imageName">{{img.titulo}}.jpg</span>
            <div class="remove-btn">
              <DefaultButton classe="remove-hover-white" confirm @click="remove($event, img)">Remover</DefaultButton>
            </div>
          </div>
          <!-- <painel :titulo="img.titulo">
              <img  class="dogImage" :src="img.url"  @click="downloadFile(img.url)" :alt="img.titulo">
            </painel> -->
        </li>
    </ul>
  </div>
</template>

<script>
import Painel from '../shared/painel/Painel.vue'
import DefaultButton from '../shared/defaultButton/DefaultButton.vue'
import DefaultInput from '../shared/defaultInput/DefaultInput.vue'
export default {
  name: 'home',
  components:  {
    Painel,
    DefaultButton,
    DefaultInput
  },
  data () {
    return {
      showName: false,
      welcome: 'Bem vindo',
      title: 'AluraPic',
      name: 'Thiago',
      photos: [],
      filtro:''
    }
  },
  created() {
    //get, dps conversão pra json dps recebimento no photos
    const teste = this.$http.get('http://localhost:3000/v1/fotos')
      .then (res => res.json())
      .then(img => this.photos=img, err => console.error(err));
  },
  computed: {
    filterPhotos() {
      if (this.filtro) {
        let exp = new RegExp(this.filtro.trim(), 'i');
        return this.photos.filter( photo => exp.test(photo.titulo));
      } else {
        return this.photos;
      }

    }
  },
  methods:{
    downloadFile(value) {
      window.open(value)
    },
    redirect() {
      this.$router.push("/cadastro");
    },
    remove($event, value) {
      
      alert(`${value.titulo} removido!\n ${$event}`);
    }
  }
}
</script>

<style>
.welcome {
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
  font-size: 35px;
  color: #fff;
  font-weight: 700;
  margin-right: 36px;
}
.remove-btn {
  margin-left: 2.1rem;
}
.view-container {
  position: relative;
  width: 70%;
}
.header {
  display: flex;
  justify-content: space-between;
  padding: 0 7px 0 26px;
}
.imageDisp {
  flex-wrap: wrap;
  align-self: center;
  justify-content: center;
  display: flex;
}

.imageWrapper {
  display: block;
  filter: brightness(.95);
  background-color: #fff9f9;
  border: 1px solid;
  width: 420px;
  height: 364px;
  border-radius: 20px;
  margin: 0 0px 15px;
  padding: 0px 0px 25px;
}

.dogImage {
  width: 350px;
  height: 310px;
  cursor: default;
  align-self: center;
  margin-top: 8%;
  margin-right: 3%;
  margin-left: 4%;
  justify-self: center;
} 
.dogImage:hover {
  filter: brightness(.25);
  cursor:pointer;
}
.pesquisa{
  display: block;
  width: 93%;
  border-radius: 8px;
  height: 30px;
  border: 1px solid #3498db;
  outline: 0;
  margin: 5px;
}
.imageName {
 color:#f0efef;
 font-weight: 600;
 position: absolute;
 right: 13%;
 bottom: 12%;
}
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
