<template>
  <div>
    <!-- Header -->
    <div class="index-header-usuario">
      <div class="index-sub-header-usuario">
        <p class="index-header-texto-usuario-1">Alcaldía de Medellín</p>
        <p class="index-header-texto-usuario-2">Escuela Virtual de Aprendizaje</p>
      </div>
    </div>
    <!-- FIN Header -->

    <CpNavUsuario
      @cambiarPestana="cambiarPestana"
    />

    <!-- Visualización del contenido -->
    <div class="container container-b">
      <div class="mt-3">
        <div id="miga">{{usuario}} > {{this.pestanaActiva}} > {{this.categoriaActiva}}</div>
      </div>
      <CpCursos
        v-if="pestanaCursos"
        :servidor="servidor"
        :ciudadania="ciudadania"
        @cambioCategoria="cambioCategoria"
      />
      <CpConoceMas v-if="pestanaConoceMas" />
      <CpCifras v-if="pestanaCifras" />
    </div>
    <!-- FIN Visualización del contenido -->

    <CpFooter />
  </div>
</template>

<script>
import CpNavUsuario from '../components/CpNavUsuario.vue'
import CpConoceMas from '../components/CpConoceMas.vue'
import CpCursos from '../components/CpCursos.vue'
import CpFooter from '../components/CpFooter.vue'
import CpCifras from '../components/CpCifras.vue'

export default {
  name: 'ViewIndexUsuario',
  data () {
    return {
      pestanaActiva: 'Cursos',
      categoriaActiva: '',
      pestanaCursos: true,
      pestanaConoceMas: false,
      pestanaCifras: false
    }
  },
  components: {
    CpNavUsuario,
    CpConoceMas,
    CpCursos,
    CpFooter,
    CpCifras
  },
  props: ['usuario', 'servidor', 'ciudadania'],
  methods: {
    cambiarPestana (nombreMiga, pestanaCursos, pestanaConoceMas, pestanaCifras) {
      this.pestanaActiva = nombreMiga
      this.pestanaCursos = pestanaCursos
      this.pestanaConoceMas = pestanaConoceMas
      this.pestanaCifras = pestanaCifras
      this.categoriaActiva = ''
    },
    cambioCategoria (categoriaActiva) {
      this.categoriaActiva = categoriaActiva
    }
  }
}
</script>
