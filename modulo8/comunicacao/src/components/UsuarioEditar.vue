<template>
    <div class="componente">
        <h2>Alterar os Dados de Usuário</h2>
        <p>Edite as informações</p>
        <button @click="alterarIdade"></button>
        <p>Idade : {{ idade }} </p>
    </div>
</template>

<script>

import barramento from '../barramento'

export default {
    props:['idade'],
    methods:{
        alterarIdade(){
            this.idade = 33
            barramento.alterarIdade(33)
        }
    }
}
</script>

<style scoped>
    .componente {
        flex: 1;
        background-color: #98b99a;
        color: #fff;
        border-radius: 6px;
    }
</style>
