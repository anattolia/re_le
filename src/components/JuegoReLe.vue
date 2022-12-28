<template>
  <div id="escena">
  <div id="titulo">
    <h1>{{ escena.titulo }}</h1>
  </div>
  <div v-if="escena.escenaDer !== null" class="opciones">
    <div id="opcion" @click="cargarEscena(escena.escenaIzq)">
      <p  class="descripcion">{{ escena.descripcionIzq }}</p>
   
      <img :src="`${urlImagen(escena.imagenIzq)}`" alt="no se ve" />
    </div>
    <div id="opcion" @click="cargarEscena(escena.escenaDer)">
      <p class="descripcion">{{ escena.descripcionDer }}</p>
      <img :src="`${urlImagen(escena.imagenDer)}`" alt="no se ve" />
    </div>
  </div>
  <div v-else>
    <div id="opcionUnica" @click="cargarEscena(escena.escenaIzq)">
      <img id="imagen" :src="`${urlImagen(escena.imagenIzq)}`" alt="no se ve" />
    </div>
  </div>
</div>
</template>

<script>
import escenas from '../escenas.json';
export default {
  data() {
    return {
      escenasJSON: escenas,
      escena: {
        numero: null,
        titulo: '',
        descripcionIzq: '',
        descripcionDer: '',
        imagenIzq: '',
        imagenDer: '',
        escenaIzq: null,
        escenaDer: null,
        imagen: null,
      },
    };
  },

  created() {
    this.cargarEscena(1);
  },

  methods: {
    cargarEscena(i) {
      console.log("escena", i)
      this.escena.numero = i;
      this.escena.titulo = this.escenasJSON.escenas[i].titulo;
      this.escena.descripcionIzq = this.escenasJSON.escenas[i].descripcion_izq;
      this.escena.descripcionDer = this.escenasJSON.escenas[i].descripcion_der;
      this.escena.imagenIzq = this.escenasJSON.escenas[i].imagen_izq;
      this.escena.imagenDer = this.escenasJSON.escenas[i].imagen_der;
      this.escena.escenaIzq = this.escenasJSON.escenas[i].escena_izq;
      this.escena.escenaDer = this.escenasJSON.escenas[i].escena_der;
    },
    urlImagen(img) {
        return `${require(`../assets/${img}.png`)}`;
    },
  },
};
</script>

<style scoped>
@import url('https://fonts.googleapis.com/css2?family=Prosto+One&display=swap');
#escena {
  font-family: 'Prosto One', cursive;
}
.opciones {
  display: flex;
  width: 90%;
  left: 10%;
  justify-content: center;
  margin: 1em auto;
}
.opciones #opcion {
  width: 40%;
  height: auto;
  padding: 2%;
  font-size: 1.2vw;
  cursor: pointer;
}
.opciones img {
  width: 100%;
}
#titulo {
font-size: 0.9em;
}
.descripcion {
  position: absolute;
  width: 24%;
  margin: 10% 5%;
  font-size: 1.5em;
  background-color: rgba(255, 255, 255, 0.5);
  padding: 0.5em;
  color: black;
}
#opcionUnica {
  
}
#imagen {
    height: 75vh;
}
</style>
