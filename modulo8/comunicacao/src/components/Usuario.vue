<template>
    <div class="container">
        <h1>Componente Usuário</h1>
        <p>Esse é um componente muito legal!</p>
        <p>Nome -> {{ nome }}</p>
        <p>Idade -> {{ idade }}
        <hr>
        
        <div class="componentes">
            <app-usuario-info :nome="nome" @nomeMudou="nome = $event" :reiniciarFn="reiniciarNome" :idade="idade" />
            <app-usuario-editar :idade="idade" @idadeMudou="idade = $event" />
        </div>
    </div>
</template>

<script>
import AppUsuarioInfo from './UsuarioInfo'
import AppUsuarioEditar from './UsuarioEditar'

export default {
async created() {
    const response = await fetch("https://api.npms.io/v2/search?q=vue")
    const data = await response.json()
    this.totalVuePackages = data.total
  },data(){
        return {
            nome: "",
            idade: 0
        }
    },
    methods:{
        
            reiniciarNome(){
                this.nome = "Pedro"
            }

        
    } ,
    components: { AppUsuarioInfo, AppUsuarioEditar }
}
</script>

<style scoped>
    .container {
        background-color: #27363b;
        color: #fff;
        padding: 10px;
        border: 1px black;
        border-radius:6px;
    }

    .container hr {
        margin: 20px 10px;
    }

    .componentes {
        display: flex;
    }

    .componentes > * {
        margin: 10px;
    }
</style>
