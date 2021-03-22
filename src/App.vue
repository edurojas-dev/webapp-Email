<template>
  <div id="app" class="container mt-5">
    <div class="">
      <h1 class="text-center titulo">
        <img src="./assets/mail.png" alt="mail" class="img-fluid">
        <br>
        WebApp Email List
      </h1>
      <hr>
      <cadastrarUsers />
      <br>
      <tabelaUsers />
    </div>

  </div>
</template>

<script>
import cadastrarUsers from './components/cadastrarUsers'
import tabelaUsers from './components/tabelaUsers.vue'
export default {
  name: 'App',
  components: {
    cadastrarUsers,
    tabelaUsers
  }
}
</script>

<style>
@import url('https://fonts.googleapis.com/css2?family=Roboto+Slab:wght@500&display=swap');

body{
  /* background-color: #2c3e50; */
  background-image: url('./assets/bg.jpg');
  background-position: center;
  background-repeat: no-repeat;
  background-size: cover;
  background-attachment: fixed;
  height: 100vh;
}

.titulo{
  font-family: 'Roboto Slab', serif;
  color: #2c3e50;
}
</style>
