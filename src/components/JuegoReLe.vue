<template>
  <div id="escena">
    <div v-if="escena.numero === 15">
      <h1 id="fin">{{ escena.titulo }}</h1>
    </div>
    <div v-else>
      <div>
        <h1 id="titulo">{{ escena.titulo }}</h1>
      </div>
      <div v-if="escena.escenaDer !== null" class="opciones">
        <div id="opcion" @click="cargarEscena(escena.escenaIzq)">
          <p class="descripcion">{{ escena.descripcionIzq }}</p>

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
  </div>
</template>

<script>
import escenas from '../escenas.json';
let escenaAnterior = 0;

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
    this.pintarCucaracha();
  },

  methods: {
    cargarEscena(i) {
      if (i === 0) {
        this.escena.titulo = this.escenasJSON.escenas[escenaAnterior].texto_muerte;
      } else {
        this.escena.titulo = this.escenasJSON.escenas[i].titulo;
      }
      this.escena.numero = i;
      this.escena.descripcionIzq = this.escenasJSON.escenas[i].descripcion_izq;
      this.escena.descripcionDer = this.escenasJSON.escenas[i].descripcion_der;
      this.escena.imagenIzq = this.escenasJSON.escenas[i].imagen_izq;
      this.escena.imagenDer = this.escenasJSON.escenas[i].imagen_der;
      this.escena.escenaIzq = this.escenasJSON.escenas[i].escena_izq;
      this.escena.escenaDer = this.escenasJSON.escenas[i].escena_der;

      escenaAnterior = this.escena.numero;
    },
    urlImagen(img) {
      return `${require(`../assets/${img}.png`)}`;
    },
    pintarCucaracha() {
      console.log(
        '     Estamos bien\n',
        " ,--.       ,---. \r\n  /    '.    /     \\ \r\n         \\  ; \r\n          \\-| \r\n         (o o)      (/ \r\n         /'v'     ,-' \r\n ,------/ >< \\---' \r\n/)     ;  --  : \r\n   ,---| ---- |--. \r\n  ;    | ---- |   : \r\n (|  ,-| ---- |-. |) \r\n    | /| ---- |\\ | \r\n    |/ | ---- | \\| \r\n    \\  : ---- ;  | \r\n     \\  \\ -- /  / \r\n     ;   \\  /  : \r\n    /   / \\/ \\  \\ \r\n   /)           (\\ "
      );
    },
  },
};
</script>

<style scoped>
@import url('https://fonts.googleapis.com/css2?family=VT323&display=swap');
#fin {
  display: flex;
  justify-content: center;
  padding-top: 25vh;
}
#escena {
  font-family: 'VT323', monospace;
}
#titulo {
  font-size: 1.5em;
  margin: 1em;
}
.opciones {
  display: flex;
  flex-direction: column;
  width: 90%;
  margin: 0 5%;
  justify-items: center;
}
.opciones #opcion {
  height: auto;
  padding: 2%;
  font-size: 1.2em;
  cursor: pointer;
}
.opciones img {
  width: 90%;
}
.descripcion {
  position: absolute;
  width: 60%;
  margin: 25% 10%;
  font-size: 1.2em;
  background-color: rgba(255, 255, 255, 0.6);
  padding: 0.5em;
  color: black;
}
#opcionUnica #imagen {
  height: 75vh;
  cursor: pointer;
}

@media (min-width: 1200px) {
  #titulo {
    font-size: 1.7em;
    margin: 1em 5em;
  }
  .opciones {
    flex-direction: row;
    justify-content: center;
    margin: 1em auto;
    left: 10%;
  }
  .opciones #opcion {
    width: 40%;
  }
  .opciones img {
    width: 90%;
  }
  .descripcion {
    width: 24%;
    margin: 10% 5%;
  }
}
</style>
