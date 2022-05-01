<template>
  <div v-if="jugar">
    <JuegoReLe />
  </div>
  <div v-else>
    <InicioJuego :actualizarEstado="actualizarEstado" />
  </div>
</template>

<script>
import InicioJuego from './components/InicioJuego.vue'
import JuegoReLe from './components/JuegoReLe.vue'

export default {
  name: 'App',
  components: {
    InicioJuego, JuegoReLe
  },
  data() {
    return {
      jugar: false,
    };
  },
  methods: {
    actualizarEstado() {
      this.jugar = !this.jugar;
    },
  },
}
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
