<script>
import Formulario from './components/Formulario.vue'
import Listado from './components/Listado.vue'
export default {
  components: {
    Formulario,
    Listado,

  },
  data() {
    return {
      datos: [],
      detalle: null,
    }
  },
  methods: {
    enviarDatos(dato) {
      this.datos.push(dato)
    },
    eliminarDato(index) {
      this.datos.splice(index, 1);
    }
  }
}
</script>

<template>
  <div class="container">
    <div class="form">
      <Formulario @enviar-datos="enviarDatos">

      </Formulario>
    </div>
    <div class="list">
      <Listado :datos="datos" @eliminar-dato="eliminarDato"></Listado>
    </div>
  </div>
</template>

<style scoped>
.container {
  width: 100%;
  display: block;
  

}
.list {
  width: 100%;
  display: grid;
  

}
</style>
