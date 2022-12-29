<template>
  <div v-if="jugar">
    <JuegoReLe />
  </div>
  <div v-else>
    <InicioJuego :actualizarEstado="actualizarEstado" />
  </div>
</template>

<script>
import InicioJuego from './components/InicioJuego.vue';
import JuegoReLe from './components/JuegoReLe.vue';

export default {
  name: 'App',
  components: {
    InicioJuego,
    JuegoReLe,
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
};
</script>

<style>
body {
  margin: 0;
  background-color: rgb(18, 18, 18);
  color: white;
}
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  margin-top: 60px;
}
</style>
