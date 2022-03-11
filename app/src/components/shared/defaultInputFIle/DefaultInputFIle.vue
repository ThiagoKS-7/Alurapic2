<template>
<div class="file-label">
  <input type="file" name="arquivo" id="arquivo">
  <label for="arquivo">Enviar arquivo</label>
</div>
</template>

<script>
export default {
  name:'DefaultInputFile',
  props: {
    classe: {
      type:String
    },
    placeholder: {
      type:String,
    }
  }
}
</script>

<style>
body {
    font-family: Helvetica;
}
body {
    font-family: Helvetica;
}
input[type="file"] {
    opacity: 0;
    
}
.file-label {
    padding: 5px 10px 20px;
    width: 200px;
    background-color: #333;
    color: #FFF;
    text-transform: uppercase;
    text-align: center;
    display: block;
    cursor: pointer;
    margin-top: 10px;  
}
</style>