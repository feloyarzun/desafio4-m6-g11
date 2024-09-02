<script>
import CitaCard from './CitaCard.vue'

export default {
  props: ['citas'],
  components: {
    CitaCard
  },
  methods: {
    eliminarCita(idx) {
      this.$emit('eliminar-cita', idx)
    }
  }
}
</script>

<template>
  <div class="citas-lista">
    <p v-if="citas.length === 0" class="sin-citas">Aún no hay consultas registradas</p>
    <CitaCard
      v-for="(cita, idx) in citas"
      :key="idx"
      :cita="cita"
      :idx="idx"
      @eliminar-cita="eliminarCita"
    />
  </div>
</template>

<style scoped>
.citas-lista {
  display: flex;
  flex-wrap: wrap;
  gap: 10px;
  justify-content: space-evenly;
}

.sin-citas {
  color: red;
}
</style>
