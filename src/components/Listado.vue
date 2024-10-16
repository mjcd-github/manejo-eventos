<script>
export default {
    props: ['datos'],

    data() {
        return {
            gravedad: ''
        }
    }
}
</script>

<template>
    <div id="listado">
        <div v-for="(paciente, index) in datos" :key="index" :class="{
            'baja': paciente.gravedad == 'Baja',
            'media': paciente.gravedad == 'Media',
            'alta': paciente.gravedad == 'Alta'
        }">
            <span>Paciente</span>
            <p>{{ paciente.paciente }}</p>
            <span>Fecha</span>
            <p>{{ paciente.fecha }}</p>
            <span>Hora</span>
            <p>{{ paciente.hora }}</p>
            <span>Motivo</span>
            <p>{{ paciente.motivo }}</p>
            <button class="btn btn-light " @click="$emit('eliminar-dato', index)">Eliminar</button>

        </div>


    </div>
    <div class="alerta" v-if="!datos.length" :style="{ color: 'red' }">
        <h5>Aún no hay consultas registradas</h5>
    </div>
</template>

<style scoped>
#listado {
    width: 100%;
    display: grid;
    grid-template-columns: repeat(5, 1fr);
    gap: 20px;
    place-items: center;
    margin: 10px;
    text-align: center;
    font-size: 14px;
    border-radius: px;


}

.baja {
    background-color: rgb(105, 235, 29);
    margin-right: 10px;
    width: 150px;
    border-radius: 5px;
}

.media {
    background-color: yellow;
    color: black;
    margin-right: 10px;
    width: 150px;
    border-radius: 5px;
}

.alta {
    background-color: red;
    color: white;
    margin-right: 10px;
    width: 150px;
    border-radius: 5px;
}

.btn {
    margin: 5px;

}

span {
    font-weight: 600;

}

.alerta {
    width: 100%;
    text-align: center;
    margin: 10px;

}
</style>