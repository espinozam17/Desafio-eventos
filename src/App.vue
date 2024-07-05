<template>
  <div id="app" class="container">
    <main>
      <h1>Citas médicas</h1>
      <form  @submit.prevent="agregarCita">
        <div >
          <!--pacientes-->
          <div>
            <label
              for=""
              class="form-label"
              :class="!cita.paciente ? '' : ''"
              >Paciente:
            </label>
            <input type="text" class="form" v-model="cita.paciente" />
          </div>
          <!--fecha-->
          <div>
            <label
              for=""
              class="form"
              :class="!cita.fecha ? '' : ''"
            >
              Fecha:
            </label>
            <input type="date" class="form" v-model="cita.fecha" />
          </div>
          <!--hora-->
          <div>
            <label
              for=""
              class="form-label"
              :class="!cita.hora ? '' : ''"
              >Hora:
            </label>
            <input type="time" class="form" v-model="cita.hora" />
          </div>
          <!--gravedad-->
          <div>
            <label
              for=""
              class="form-label"
              :class="!cita.gravedad ? '' : ''"
              >Gravedad:
            </label>
            <select name="" id="" class="form" v-model="cita.gravedad">
              <option
                :value="gravedad"
                v-for="(gravedad, index) in gravedades"
                :key="index"
              >
                {{ gravedad }}
              </option>
            </select>
          </div>
          <!--motivo-->
          <div>
            <label
              for=""
              class="form-label"
              :class="!cita.motivo ? '' : ''"
              >Motivo:
            </label>
            <input type="text" class="form" v-model="cita.motivo" />
          </div>
        </div>
        <div >
          <button
            type="submit"
            class="btn"
            :disabled="
              !cita.paciente ||
              !cita.fecha ||
              !cita.hora ||
              !cita.gravedad ||
              !cita.motivo
            ">Agregar
          </button>
        </div>
      </form>
     <div>
        <p  v-if="citas.length < 1">
          Aún no hay consultas registradas
        </p>
        <div v-else class="row g-3">
          <div  v-for="(cita, index) in citas" :key="index">
            <CardsCita :cita="cita" @EliminarCita="eliminarCitaHandler(index)" />
          </div>
        </div>
      </div>
    </main>
  </div>
</template>

<script>
import CardsCita from "./components/CardsCita";
export default {
  name: "App",
  components: {
    CardsCita,
  },
  data() {
    return {
      citas: [],
      cita: {
        paciente: "",
        fecha: "",
        hora: "",
        gravedad: "",
        motivo: "",
      },
      gravedades: ["Baja", "Media", "Alta"],
    };
  },
  methods: {
    agregarCita() {
      this.citas.push(this.cita);
      this.cita = {};

    },
     eliminarCitaHandler(index) {
      if (confirm("Estas seguro que deseas eliminar esta cita?")) {
        this.citas.splice(index, 1);

     }
    },
  },
  computed: {},
};
</script>

<style>

</style>