<template>
  <div id="tabela">
    <div class="container p-3 bg-light">
        <table class="table table-hover">
            <thead>
                <tr>
                    <th scope="col">Nome</th>
                    <th scope="col">E-mail</th>
                    <th scope="col">Deletar</th>
                </tr>
            </thead>
            <tbody>
                <tr v-for="item in listaDados" :key="item">
                    <td>{{item.nome}}</td>
                    <td>{{item.email}}</td>
                    <td>
                        <button class="btn btn-dark" type="button" v-on:click="deletarDados(item.valID)">
                            Deletar
                        </button>
                    </td>
                </tr>
            </tbody>
        </table>
    </div>
    <div class="container mt-3">
        <center>
            <button class="btn btn-danger" v-on:click="limparTudo">Limpar Lista</button>
        </center>
    </div>
  </div>
</template>

<script>
import $ from 'jquery'
export default {
    name: 'tabelaUsers',
    data(){
        return {
            valorLocal : localStorage.getItem('qtdIds'),
            listaDados: []
        }
    },
    methods:{
        chamarDados(){
            let transInt = parseInt(this.valorLocal)
            for(var i = 1; i <= transInt; i++){
                let emais = JSON.parse(localStorage.getItem(i))
                console.log(emais)
                if(emais == null){continue}
                this.listaDados.push({
                    valID: emais.valID,
                    nome: emais.nome,
                    email: emais.email
                })
            }
        },

        deletarDados(ix){
            localStorage.removeItem(ix)
            location.reload()
        },

        limparTudo(){
            localStorage.clear()
            $("#tabela").hide()
            setTimeout(() => {
                location.reload()
            }, 800);
        }
    },
    created(){
        console.log("Rodando aplicação Vue.js")
        this.chamarDados()
        $(document).ready(()=>{
           const validacao = localStorage.getItem("qtdIds")
           if(validacao == "0"){$("#tabela").hide()}           
        })
          
    },
}
</script>

<style>
.bg-light{
    /* background-color: #bdbfc0; */
    border-radius: 15px;
    box-shadow: 10px 10px 10px black;
}
</style>
