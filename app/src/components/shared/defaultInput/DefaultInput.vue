<template>
<div>
   <input type="search" id="arquivo" @input="$emit('input', $event)"  class="filtro" :class="classe" :placeholder="placeholder">
</div>
</template>

<script>
export default {
  props: {
    classe: {
      type:String
    },
    placeholder: {
      type:String,
      required:true
    }
  }
}
</script>

<style>
.filtro {
  display: block;
  width: 31rem;
  border-radius: 8px;
  height: 30px;
  border: 1px solid #3498db;
  outline: 0;
}

.filtro:focus
{
    border:  solid 1px #3124e2;
    outline: 0;
}

.filtro-sidebar{
  display: block;
  width: 93%;
  border-radius: 8px;
  height: 30px;
  border: 1px solid #3498db;
  outline: 0;
  margin: 5px;
}
</style>