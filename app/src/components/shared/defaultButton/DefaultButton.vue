<template>
  <button class="btn" :class="classe" @click="onClick()"><slot></slot></button>
</template>

<script>
export default {
  name:'DefaultButton',
  props: {
    tipo: {
      type: String,
    },
    classe: {
      type: String,
      default:"normal"
    },
    confirm: {
      type:Boolean,
      default:false
    }
  },
  methods: {
    onClick() {
      if(this.confirm) {
        if(confirm('Tem certeza disso?')) {
          this.$emit("click", new Date());
        }
      } else {
        this.$emit("click");
      }

    }
  }
}
</script>

<style>
.btn {
  box-sizing: border-box;
    -webkit-appearance: none;
    -moz-appearance: none;
    appearance: none;
    background-color: transparent;
    border-radius: 0.6em;
    cursor: pointer;
    display: -webkit-box;
    display: -webkit-flex;
    display: -ms-flexbox;
    display: flex;
    -webkit-align-self: center;
    -ms-flex-item-align: center;
    align-self: center;
    font-size: 0.8rem;
    font-weight: 400;
    line-height: 1;
    padding: 0.6em 1.8em;
    text-decoration: none;
    text-align: center;
    text-transform: uppercase;
    font-family: 'Montserrat', sans-serif;
    font-weight: 700;
    margin-right: 20px;
}
.btn:hover, .btn:focus {
  color: #fff;
  outline: 0;
}
.normal {
  border-color: #3498db;
  color: #fff;
  box-shadow: 0 0 40px 40px #3498db inset, 0 0 0 0 #3498db;
  -webkit-transition: all 150ms ease-in-out;
  transition: all 150ms ease-in-out;
}
.normal:hover {
  box-shadow: 0 0 10px 0 #3124e2 inset, 0 0 10px 4px #3124e2;
}

.remove {
  border-color: #ee0d0d;
  color: #fff;
  box-shadow: 0 0 40px 40px #ee0d0d inset, 0 0 0 0 #ee0d0d;
  -webkit-transition: all 150ms ease-in-out;
  transition: all 150ms ease-in-out;
}
.remove:hover {
  box-shadow: 0 0 10px 0 #e78708 inset, 0 0 10px 4px #e78708 ;
}

.remove-hover-white {
  border-color: #ee0d0d;
  color: #fff;
  box-shadow: 0 0 40px 40px #ee0d0d inset, 0 0 0 0 #ee0d0d;
  -webkit-transition: all 150ms ease-in-out;
  transition: all 150ms ease-in-out;
}
.remove-hover-white:hover {
  background-color: #fff;
  box-shadow: 0 0 10px 0 #e78708 inset, 0 0 10px 4px #e78708;
  color: #000 !important;
}
</style>