<template>
  <h1>Un juego sobre Aprendizaje por Refuerzo ('Reinforcement Learning')</h1>
  <div>Descripción del proyecto</div>
  <button @click="actualizarEstado">Comenzar</button>
</template>

<script>
export default {
  props: {
    actualizarEstado: {
      type: Function,
      default: () => {},
    },
  },
};
</script>

<style>
</style>