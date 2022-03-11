<template>
    <div class="centralizado">
        <h2 class="centralizado cadastro">Cadastro de imagens</h2>
        <div class="form-field">
            <label class="label-field">Nome da imagem: </label>
            <DefaultInput @input="filtro = $event.target.value" placeholder=" Nome da imagem"/>
        </div>
        <div class="form-field">
            <label class="label-field-url">Url da imagem:   </label>
            <DefaultInput @input="filtro = $event.target.value" placeholder=" Url da imagem"/>
        </div>
        <div class="footer">
            <DefaultButton @click="goBack()">voltar</DefaultButton>
            <DefaultButton @click="save()">Salvar</DefaultButton>
        </div>
        <!-- <DefaultInputFile @input="filtro = $event.target.value"/> -->
        
    </div>
</template>

<script>
import DefaultButton from '../shared/defaultButton/DefaultButton.vue'
import DefaultInput from '../shared/defaultInput/DefaultInput.vue'
import DefaultInputFile from '../shared/defaultInputFIle/DefaultInputFIle.vue'
export default {
    name:'Cadastro',
    components: {
        DefaultButton,
        DefaultInput,
        DefaultInputFile
    },
    methods: {
        goBack() {
            this.$router.push("/");
        },
        save() {
            alert("salvo!");
        }
    }
}
</script>

<style scoped>
.cadastro {
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
  font-size: 35px;
  color: #fff;
  font-weight: 700;
}
.centralizado {
    text-align: center;
    display: flex;
    flex-direction: column;
    align-self: center;
    align-items: center;
    position: relative;
    width: 70%;
}

.form-field {
    width: 100%;
    display: flex;
    align-items: center;
    margin-bottom: 20px;
    justify-content: space-around;
}
.label-field {
    font-family: 'Avenir', Helvetica, Arial, sans-serif;
    font-size: 20px;
    color: #fff;
    font-weight: 700;
}
.label-field-url {
    font-family: 'Avenir', Helvetica, Arial, sans-serif;
    font-size: 20px;
    color: #fff;
    font-weight: 700;
    margin-right: 26px;
}
.footer {
    display: flex;
    width: 90%;
    justify-content: flex-end;
}
</style>