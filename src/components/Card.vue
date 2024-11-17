<script>
    export default {
        props: {
            paciente: String,
            fecha: String,
            hora: String,
            gravedad: String,
            motivo: String,
            index: Number, // Recibe el índice de la cita
        },
        methods: {
            gravedadColor(gravedad) {
                switch (gravedad) {
                    case 'Baja':
                    return { backgroundColor: '#ffff00', color: '#000' }; // Amarillo
                    case 'Media':
                    return { backgroundColor: '#adff2f', color: '#000' }; // Verde
                    case 'Alta':
                    return { backgroundColor: '#ff0000', color: '#fff' }; // Rojo
                    default:
                    return { backgroundColor: '#6c757d', color: '#fff' }; // Gris por defecto
                }
            },
            eliminarCita() {
                this.$emit('eliminar-cita', this.index); // Emite el índice al padre para la eliminación del arreglo dónde se están registrando las consultas
            },
        },
    };
</script>

<template>
    <div class="card mb-4" :style="gravedadColor(gravedad)">
        <h6 class="fw-bold mt-3 card-title">Paciente:</h6>
        <h4 class="mb-4 card-text">{{ paciente }}</h4>
        <h6 class="fw-bold m-0 p-0">Fecha:</h6>
        <p class="card-text">{{ fecha }}</p>
        <h6 class="fw-bold m-0 p-0">Hora:</h6>
        <p class="card-text">{{ hora }}</p>
        <h6 class="fw-bold m-0 p-0">Motivo:</h6>
        <p class="card-text mb-4">{{ motivo }}</p>
        <button class="btn btn-light btn-sm shadow w-100 border border-secondary-subtle" @click.prevnet="eliminarCita">Eliminar</button> 
        <!-- .prevent Modificador para evitar el envío del formulario -->
    </div>
</template>