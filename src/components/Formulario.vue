<script>
export default {
    name: 'App',

    data() {
        return {    
            gravedad:"",
            tipoGravedad:["Baja","Media","Alta"],
            paciente: "",
            fecha: "",
            hora: "",
            motivo: "",
            
              }
    },
    methods: {
        enviarDatos() {
            this.$emit('enviar-datos', {
                gravedad: this.gravedad,
                paciente: this.paciente,
                fecha: this.fecha,
                hora: this.hora,
                motivo: this.motivo,
            },
        this.limpiar());
          },
          limpiar() {
            this.gravedad = "";
            this.paciente = "";
            this.fecha = "";
            this.hora = "";
            this.motivo = "";
          }
    },
    computed: {
        verificarInput() {
            return this.paciente.trim() && this.fecha.trim() && this.hora.trim() && this.gravedad.trim() && this.motivo.trim()
        }
    }
}
</script>

<template>
<div class="container">
    <form @submit.prevent>
        <div class="formulario col-sm-12">
        <div class="element">
            <label :class="{'red':!paciente}">Paciente</label>
            <input type="text" v-model="paciente">
        </div>
        <div class="element">
            <label :class="{'red':!fecha}">Fecha</label>
            <input type="date" v-model="fecha">
        </div>
        <div class="element">
            <label :class="{'red':!hora}">Hora</label>
            <input type="time" v-model="hora">
        </div>
        <div class="element">
            <label :class="{'red':!gravedad}">Gravedad</label>
            <select v-model="gravedad">
                <option v-for="gravedad in tipoGravedad">{{ gravedad }}</option>                
            </select>
        </div>
        <div class="element">
            <label :class="{'red':!motivo}">Motivo</label>
            <input type="text" v-model="motivo">
        </div>
        </div>
        

        <div class="boton col-sm-12" >
            <button class="btn btn-success" :disabled="!verificarInput" @click="enviarDatos">Agregar</button>
        </div>
        
    </form>
</div>

</template>

<style scoped>

.container {
    width: 80%;
    margin-top: 20px;
    display: flex;
    justify-content: center;
    border: 1px solid black;
    border-radius: 10px;
    
}
form {
    width: 100%;
    text-align: center;
    
 
 
}
.formulario{
    display: flex;
    justify-content: center;
}
.element {
    display: flex;
    flex-direction: column;
    margin: 10px;
    width: auto;
    
}
.red {
    color: red;
}
label {
    font-weight: bold;
}
</style>