<script>
export default {
  data() {
    return {
      paciente: '',
      fecha: '',
      hora: '',
      gravedad: '',
      motivo: '',
      formValido: false
    }
  },
  methods: {
    validarForm() {
      this.formValido =
        this.paciente !== '' &&
        this.fecha !== '' &&
        this.hora !== '' &&
        this.gravedad !== '' &&
        this.motivo !== ''
    },
    enviarCita() {
      this.$emit('nueva-cita', {
        paciente: this.paciente,
        fecha: this.fecha,
        hora: this.hora,
        gravedad: this.gravedad,
        motivo: this.motivo
      })
      this.limpiarForm()
    },
    limpiarForm() {
      this.paciente = ''
      this.fecha = ''
      this.hora = ''
      this.gravedad = ''
      this.motivo = ''
      this.formValido = false
    }
  }
}
</script>

<template>
  <form @submit.prevent="enviarCita">
    <div class="form-row">
      <div class="form-group">
        <label for="paciente" :class="paciente === '' ? 'invalid' : ''">Paciente</label>
        <input type="text" v-model="paciente" id="paciente" required />
      </div>

      <div class="form-group">
        <label for="fecha" :class="fecha === '' ? 'invalid' : ''">Fecha</label>
        <input type="date" v-model="fecha" id="fecha" required />
      </div>

      <div class="form-group">
        <label for="hora" :class="hora === '' ? 'invalid' : ''">Hora</label>
        <input type="time" v-model="hora" id="hora" required />
      </div>

      <div class="form-group">
        <label for="gravedad" :class="gravedad === '' ? 'invalid' : ''">Gravedad</label>
        <select v-model="gravedad" id="gravedad" required>
          <option value="" disabled>Seleccione la gravedad</option>
          <option value="baja">Baja</option>
          <option value="media">Media</option>
          <option value="alta">Alta</option>
        </select>
      </div>

      <div class="form-group">
        <label for="motivo" :class="motivo === '' ? 'invalid' : ''">Motivo</label>
        <input type="text" v-model="motivo" @input="validarForm" id="motivo" />
      </div>

      <div class="form-group">
        <button :disabled="!formValido" type="submit">Agregar</button>
      </div>
    </div>
  </form>
</template>

<style scoped>
.form-row {
  display: flex;
  flex-wrap: wrap;
  gap: 20px;
  align-items: flex-end;
  margin-bottom: 20px;
}

.form-group {
  display: flex;
  flex-direction: column;
}

label {
  font-weight: bold;
  color: black;
}

label.invalid {
  color: red;
}

input,
select {
  padding: 5px;
  border: 1px solid #ccc;
  border-radius: 4px;
  width: 100%;
}

button {
  padding: 10px 20px;
  background-color: #007bff;
  color: white;
  border: none;
  border-radius: 5px;
  cursor: pointer;
}

button:disabled {
  background-color: grey;
  cursor: not-allowed;
}
</style>
