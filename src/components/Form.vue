<script>
export default {
  data() {
    return {
      paciente: '',
      fecha: '',
      hora: '',
      gravedad: '',
      motivo: '',
    };
  },
  computed: {
    // Verifica si todos los campos del formulario están completos
    formCompleto() {
      return (
        this.paciente &&
        this.fecha &&
        this.hora &&
        this.gravedad &&
        this.motivo
      );
    },
  },
  methods: {
    agregarCita() {
      const nuevaCita = {
        paciente: this.paciente,
        fecha: this.fecha,
        hora: this.hora,
        gravedad: this.gravedad,
        motivo: this.motivo,
      };
      this.$emit('nueva-cita', nuevaCita); // Emitimos una nueva cita y la envía a App.vue
      this.limpiarFormulario(); // Limpiamos los campos después de agregar la cita
    },
    limpiarFormulario() {
      this.paciente = '';
      this.fecha = '';
      this.hora = '';
      this.gravedad = '';
      this.motivo = '';
    },
  },
};
</script>

<template>
  <div class="container-fluid">
    <div class="row border border-3 border-secondary rounded-3 p-1 pt-3 m-1 m-5">
      
      <!-- Paciente -->
      <div class="col-3">
        <label 
          :class="{'text-black': paciente !== '', 'text-danger': paciente === ''}" 
          class="fs-5 fw-bold">
          Paciente
        </label>
        <input type="text" class="form-control" v-model="paciente" />
      </div>

      <!-- Fecha -->
      <div class="col-2">
        <label 
          :class="{'text-black': fecha !== '', 'text-danger': fecha === ''}" 
          class="fs-5 fw-bold">
          Fecha
        </label>
        <input type="date" class="form-control" v-model="fecha" />
      </div>

      <!-- Hora -->
      <div class="col-2">
        <label 
          :class="{'text-black': hora !== '', 'text-danger': hora === ''}" 
          class="fs-5 fw-bold">
          Hora
        </label>
        <input type="time" class="form-control" v-model="hora" />
      </div>

      <!-- Gravedad -->
      <div class="col-2">
        <label 
          :class="{'text-black': gravedad !== '', 'text-danger': gravedad === ''}" 
          class="fs-5 fw-bold">
          Gravedad
        </label>
        <select class="form-select" v-model="gravedad">
          <option value="Baja">Leve</option>
          <option value="Media">Media</option>
          <option value="Alta">Severa</option>
        </select>
      </div>

      <!-- Motivo -->
      <div class="col-3">
        <label 
          :class="{'text-black': motivo !== '', 'text-danger': motivo === ''}" 
          class="fs-5 fw-bold">
          Motivo
        </label>
        <input type="text" class="form-control" v-model="motivo" />
      </div>

      <!-- Botón Agregar Cita Médica -->
      <div class="row mb-2 mt-4">
        <div class="col-12 text-center">
          <button 
            type="button" 
            class="btn btn-light border" 
            :disabled="!formCompleto" 
            @click="agregarCita">
            Agregar
          </button>
        </div>
      </div>

    </div>
  </div>
</template>

<style scoped>
/* Mantén los estilos de Bootstrap, pero si deseas ajustes personalizados aquí puedes añadirlos */

/* Cambiar color de los textos según la clase dinámica */
.text-danger {
  color: red;
}
.text-black {
  color: black;
}
</style>
