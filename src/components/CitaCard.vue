<template>
    <div>
      <p><strong>Paciente:</strong> {{ cita.paciente }}</p>
      <p><strong>Fecha:</strong> {{ cita.fecha }}</p>
      <p><strong>Hora:</strong> {{ cita.hora }}</p>
      <p><strong>Gravedad:</strong> {{ cita.gravedad }}</p>
      <p><strong>Motivo:</strong> {{ cita.motivo }}</p>
      <button @click="eliminarCita">Eliminar</button>
    </div>
  </template>
  
  <script>
  export default {
    props: {
      cita: {
        type: Object,
        required: true
      }
    },
    methods: {
      eliminarCita() {
        this.$emit('eliminar');
      }
    }
  };
  </script>
  
  <style scoped>
  /* Estilos personalizados aquí */
  </style>
  