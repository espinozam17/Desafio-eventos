<template>
  <div>
    <div v-for="(cita, index) in citas" :key="index" class="cita-card" :class="cita.gravedad.toLowerCase()">
      <CitaCard :cita="cita" @eliminar="eliminarCita(index)" />
    </div>
    <p v-if="citas.length === 0">Aún no hay citas registradas.</p>
  </div>
</template>

<script>
import CitaCard from './CitaCard.vue';

export default {
  components: {
    CitaCard
  },
  props: {
    citas: {
      type: Array,
      required: true
    }
  },
  methods: {
    eliminarCita(index) {
      const nuevasCitas = [...this.citas];
      nuevasCitas.splice(index, 1);
      this.$emit('eliminar', nuevasCitas);
    }
  }
};
</script>

<style scoped>
.baja {
  background-color: lightgreen;
}
.media {
  background-color: lightyellow;
}
.alta {
  background-color: lightcoral;
}
.cita-card {
  padding: 10px;
  margin-bottom: 10px;
}
</style>