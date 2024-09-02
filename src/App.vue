<script>
import FormularioCita from './components/FormularioCita.vue'
import CitasMedicas from './components/CitasMedicas.vue'

export default {
  data() {
    return {
      citas: []
    }
  },
  components: {
    FormularioCita,
    CitasMedicas
  },
  methods: {
    agregarCita(nuevaCita) {
      this.citas.push(nuevaCita)
    },
    eliminarCita(idx) {
      this.citas.splice(idx, 1)
    }
  }
}
</script>

<template>
  <div id="app">
    <!-- Admin de Citas Medicas -->
    <FormularioCita @nueva-cita="agregarCita" />

    <CitasMedicas :citas="citas" @eliminar-cita="eliminarCita" />
  </div>
</template>

<style scoped></style>
