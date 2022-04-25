<template>
  <div id="titulo">
    <h1>{{ escena.titulo }}</h1>
  </div>
  <div class="opciones">
    <div id="opcion" @click="cargarEscena(escena.escenaIzq)">
      <p>{{ escena.descripcionIzq }}</p>
      <!-- TODO: Arreglar url -->
      <img :src="urlImagen(escena.imagenIzq)" alt="no se ve" />
      <img src="../assets/img/prueba.jpg" />
    </div>
    <div id="opcion" @click="cargarEscena(escena.escenaDer)">
      <p>{{ escena.descripcionDer }}</p>
      <img />
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
      },
    };
  },

  created() {
    this.cargarEscena(1);
  },

  methods: {
    cargarEscena(i) {
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
      console.log(`../assets/img/${img}.jpg`);
      return `../assets/img/${img}.jpg`;
    },
  },
};
</script>

<style>
#aplicacion {
  text-align: center;
  margin: 5%;
  display: flex;
  justify-content: center;
}
.opciones {
  display: flex;
  width: 80%;
  left: 10%;
  position: fixed;
  margin-top: 1%;
  column-gap: 60px;
  justify-content: center;
}
.opciones #opcion {
  background-color: pink;
  width: 40%;
  height: auto;
  margin: 1%;
  padding: 5%;
  font-size: 1.2vw;
  cursor: pointer;
}

.opciones img {
  width: 100%;
}
</style>
