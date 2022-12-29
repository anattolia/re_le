<template>
  <h1></h1>
  <div id="introduccion">
    <p>
      El aprendizaje por refuerzo o aprendizaje reforzado es un área del
      <a href="https://es.wikipedia.org/wiki/Aprendizaje_autom%C3%A1tico">aprendizaje automático</a> inspirada en la
      <a href="https://es.wikipedia.org/wiki/Conductismo">psicología conductista</a>, cuya ocupación es determinar qué
      acciones debe escoger un agente en un entorno dado con el fin de maximizar alguna noción de "recompensa".
    </p>
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
@import url('https://fonts.googleapis.com/css2?family=VT323&display=swap');
* {
  font-family: 'VT323', monospace;
}
a {
  color: rgb(157, 221, 236);
}
button {
  background-color: #abdbea;
  font-size: 1.2em;
  cursor: pointer;
}
#introduccion {
  width: 60vw;
  margin: 4em auto;
  font-size: 1.3em;
}

@media (min-width: 768px) {
  #introduccion {
    margin: 7em auto;
    font-size: 1.5em;
  }
}
</style>
