<template>
   <div class="imageWrapper">
        <span class="imageName">{{titulo}}.jpg</span>
    </div>
</template>

<script>
export default {
  name: 'Painel',
  props: {
    titulo: {
      type: String, 
      required: true
    }
  },
  methods:{
    downloadFile(value) {
      window.open(value)
    }
  }
}
</script>

<style>
.imageWrapper {
  display: block;
  filter: brightness(.95);
  background-color: #fff9f9;
  border: 1px solid;
  width: 440px;
  border-radius: 20px;
  margin: 0 10px 20px
}


.imageName {
 color:#f0efef;
 font-weight: 600;
 position: relative;
 right: 21%;
 bottom: 6%;

}

</style>
