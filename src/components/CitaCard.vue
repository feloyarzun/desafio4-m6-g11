<script>
export default {
  props: ['cita', 'index'],
  methods: {
    eliminarCita() {
      this.$emit('eliminar-cita', this.index)
    }
  }
}
</script>

<template>
  <div :class="['cita-card', cita.gravedad]">
    <p>Paciente: {{ cita.paciente }}</p>
    <p>Fecha: {{ cita.fecha }}</p>
    <p>Hora: {{ cita.hora }}</p>
    <p>Motivo: {{ cita.motivo }}</p>
    <button @click="eliminarCita">Eliminar</button>
  </div>
</template>

<style scoped>
.cita-card {
  padding: 20px;
  border-radius: 5px;
  color: white;
  width: 30%;
  text-align: center;
}

.cita-card.baja {
  background-color: #28a745;
}

.cita-card.media {
  background-color: #ffc107;
  color: black;
}

.cita-card.alta {
  background-color: #dc3545;
}

button {
  margin-top: 10px;
  background-color: white;
  color: black;
  border: 1px solid black;
  cursor: pointer;
}

button:hover {
  background-color: black;
  color: white;
}
</style>
