<template>
  <div>
    <!-- Header -->
    <div class="home-header">
      <div class="home-header-bg align-items-center d-flex">
        <div class="d-flex w-100 justify-content-between align-items-center">
          <div class="home-header-texto">
            <p class="home-header-texto-1 m-0">
              Alcaldía de Medellín
            </p>
            <p class="home-header-texto-2 m-0">
              Escuela Virtual de Aprendizaje
            </p>
          </div>
          <div class="cursor" v-on:click="AbrirMenu">
            <img
              src="../assets/img/boton-ingreso.png"
              alt="Botón de ingreso"
              class="img-ingreso"
            />
          </div>
        </div>
      </div>
    </div>
    <!-- FIN Header -->

    <CpCarousel />
    <CpInformacionIndex />

    <CpFooter />
  </div>
</template>

<script>
import CpCarousel from '../components/CpCarousel.vue'
import CpInformacionIndex from '../components/CpInformacionIndex.vue'
import CpFooter from '../components/CpFooter.vue'

export default {
  name: 'IndexIncio',
  components: {
    CpCarousel,
    CpInformacionIndex,
    CpFooter
  },
  methods: {
    AbrirMenu () {
      document.getElementById('usuario-ingresar').style.top = '0px'
    }
  }
}
</script>
