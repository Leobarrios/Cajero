<template>
  <div>
    <div v-if="auth === false">
      <login @enter="validar"/>
    </div>
    <div v-else>
      <cajero :usuarioActivo = usuariosValidado />
    </div>
  </div>
</template>

<script>
import Cajero from './components/Cajero.vue'
import Login from './components/Login.vue'
import { parse } from 'path';

export default {
  name: 'app',
  components: {
    Cajero,
    Login
  },
  data() {
    return {
      auth: false,
      usuarios: [],
      usuariosValidado: {}
    }
  },
  mounted(){
    this.loadUsers()
  },
  methods: { 
     loadUsers: async function() {
        const data = await fetch('./usuarios.json')
        this.usuarios = await data.json()
    },
    validar( pass ){
      const cantidadUsuarios = this.usuarios.length
      for (let i = 0; i < cantidadUsuarios; i++) {
        if (this.usuarios[i].pass == pass ){
          this.auth = true 
        } 
        
      }



      /*let txt = pass
      if (txt== null || txt== "") {
        
      } else {
        if (parseInt(txt) === 1122){
          this.auth = true
        }
      }*/
    },
      checkLogin(user) {
      // eslint-disable-next-line
      console.log(user.name)
      this.auth = true
    },
  }
}
</script>

<style>
@import url('https://fonts.googleapis.com/css?family=Source+Sans+Pro');
  body {
    margin: 0;

    font-family: "Source Sans Pro", sans-serif;

    background-color: #2a333d;
}
</style>
