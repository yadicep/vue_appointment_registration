<script> 
  import Forms from './components/Form.vue';
  import Mensaje from './components/Mensaje.vue';
  import Cards from './components/Card.vue';
  import Header from './components/Header.vue';

  export default {
    components:{
      Header,
      Forms,
      Mensaje,
      Cards,
    },
    data() {
      return {
        citas: [], 
      };
    },
    methods: {
      agregarCita(cita) {
        this.citas.push(cita); // Agrega la nueva cita al array de citas
      },
      eliminarCita(index) {
        this.citas.splice(index, 1); // Eliminamos la cita usando su índice
      },
    },
  }
</script>

<template>
  <div id="app">
    <div class="border border-2 border-dark-subtle pb-5 bg-white">

      <div class="sticky-top bg-white border-bottom">  <!-- Fijé esta parte arriba para poder desplazarme hacia las citas de abajo si deseo y seguir agregando otras sin necesidad de mover la página -->
        <Header title="ADMINISTRADOR DE CITAS MÉDICAS"></Header>    <!-- Usa el componente Header.vue -->
        <Forms @nueva-cita="agregarCita"/>     <!-- Formulario para el ingreso de las citas médicas -->
      </div>
      <Mensaje v-if="citas.length === 0" title="Aún no hay consultas registradas"></Mensaje>    <!-- Mensaje reutilizable del componente Mensaje.vue cuando no hay citas -->
      <div class="container mt-4">   <!-- Visualización de las citas registradas de cada paciente --> 
        <div class="row">
          <!-- Recorre cada cita del array citas y envía las propiedades correspondientes al componente Card -->
          <div
            v-for="(cita, index) in citas"
            :key="index"
            class="col-12 col-sm-6 col-md-4 col-lg-3">
              <Cards
                :paciente="cita.paciente"
                :fecha="cita.fecha"
                :hora="cita.hora"
                :gravedad="cita.gravedad"
                :motivo="cita.motivo"
                :index="index"
                @eliminar-cita="eliminarCita"
              />
          </div>
        </div>
      </div>
     
    </div>
  </div>
</template>