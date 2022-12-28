<template>
  <h1></h1>
  <div id="introduccion">
<p>El aprendizaje por refuerzo o aprendizaje reforzado es un área del <a href="https://es.wikipedia.org/wiki/Aprendizaje_autom%C3%A1tico">aprendizaje automático</a> inspirada en la <a href="https://es.wikipedia.org/wiki/Conductismo">psicología conductista</a>, cuya ocupación es determinar qué acciones debe escoger un agente en un entorno dado con el fin de maximizar alguna noción de "recompensa".</p> 
<p>Lo siguiente es un modelo en relación a esta dinámica.</p>
</div>
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
#introduccion {
  width: 60vw;
  margin: 7em auto;
}
</style>
