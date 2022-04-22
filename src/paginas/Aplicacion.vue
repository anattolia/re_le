<script>
import Inicio from '../componentes/Inicio.vue';
import Juego from '../componentes/Juego.vue';

export default {
  components: { Inicio, Juego },
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

<template>
  <div v-if="jugar">
    <Juego />
  </div>
  <div v-else>
    <Inicio :actualizarEstado="actualizarEstado" />
  </div>
</template>

<style>
</style>