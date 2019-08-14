<template>
  <div>
    <div class="header">
      <img class="logo" src="../assets/logo.png" />
      <div class="align-left">
        <span id="nombre">Bienvenido/a</span>
        <img class="avatar" src="../assets/avatar.svg" />
      </div>
    </div>
    <div class="white-container">
      <div class="menu-container">
        <h1 class="tu-cuenta">Login</h1>
        <!-- <input v-model="emailIng" type="email" placeholder="Nombre"> -->
        <input type="password" v-model="user.pass" placeholder="contraseña">
        <button class="links" @click="enter()">Entrar</button>
      </div>
    </div>
  </div>
</template>
<script>
export default {
  name: 'Login',
  data() {
    return {
      user: {
        // email: 'nombre usuario', 
        pass: '',
      },
    }
  },
  methods: {
    enter() {
    
      this.$emit('enter',  this.user.pass )
    }
  }
}
</script>
<style>
  .align-left {
      display: flex;
      padding: 8px;
      align-items: center;
  }
  .white-container {
      display: flex;
      width: 65%;
      padding: 30px;
      margin: 0 auto;
      box-sizing: border-box;
      border: 1px solid #979797;
      border-radius: 8px;
      background-color: #fff;
  }