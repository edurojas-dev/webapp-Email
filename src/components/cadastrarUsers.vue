<template>
  <div class="jumbotron1 p-4">
    <div class="container">
        <form>
            <div class="row">
                <div class="col-md-6">
                    <div class="form-group">
                        <label for="inputNomeUsuario" class="mb-2 h5 text-white">Nome Usuário</label>
                        <input type="text" class="form-control" id="inputNomeUsuario" aria-describedby="inputNomeUsuario" placeholder="Seu Nome" required>
                    </div>
                </div>
                <div class="col-md-6">
                    <div class="form-group">
                        <label for="inputEmail" class="mb-2 h5 text-white">E-mail</label>
                        <input type="email" class="form-control" id="inputEmail" aria-describedby="inputEmail" placeholder="Seu e-mail" required>
                    </div>
                </div>
            </div>
            <div class="row mt-3">
                <div class="col-md-10">
                    <div class="alert alert-danger text-center" role="alert" id="errorMsg">
                        Dados incorretos!
                    </div>
                    <div class="alert alert-success text-center" role="alert" id="oksMsg">
                        Dados registrados com Sucesso!
                    </div>
                </div>
                <div class="col-md-2">
                    <center>
                         <button class="btn btn-dark mt-3" type="submit" v-on:click.stop.prevent='salvarEmail'>
                            Adicionar
                        </button>
                    </center>
                </div>
            </div>
        </form>
    </div>
  </div>
</template>

<script>
// import $ from 'jquery'
export default {
  name: 'cadastrarUsers',
  methods: {
    salvarEmail(){
        let nomeUser = document.getElementById("inputNomeUsuario")
        let emailUser = document.getElementById("inputEmail")
        let emailArray = emailUser.value.split('')
        // let userArray = nomeUser.value.split('')
        let errorMSG = document.getElementById("errorMsg")

        if(nomeUser.value == '' || emailUser.value == null || emailArray.indexOf("@")== -1){
            console.log("Dados Inválidos!")
            errorMSG.style.display = "block"
            errorMSG.classList.add("animated", "fadeIn")
        }else{
            // console.log(`Aqui é o array do campo email: ${emailArray} e campo nome: $`)
            let getNumber = localStorage.getItem('qtdIds')
            let valor = parseInt(getNumber) + 1
            const usuario = {
                valID : valor,
                nome: nomeUser.value,
                email: emailUser.value
            }

            localStorage.setItem('qtdIds', valor)
            localStorage.setItem(valor, JSON.stringify(usuario))
            nomeUser.value = ''; emailUser.value = ''
            errorMSG.remove()
            location.reload()
        }
    }
  },
  created(){
    setTimeout(() => {
        let getNumber = localStorage.getItem('qtdIds')
        if(getNumber == null || getNumber == ''){
            localStorage.setItem('qtdIds', '0')
        }
    }, 1000);
  }
}
</script>

<style>
.jumbotron1{
    /* background-color: #bdbfc0; */
    background-color: rgba(102, 95, 95, 0.6);

    border-radius: 15px;
    box-shadow: 10px 10px 10px black;
}
#errorMsg, #oksMsg{
    display: none;
}
</style>
