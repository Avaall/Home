<template>
  <div id="app">
    <!-- Home ingreso que desciende -->
    <div class="position-fixed usuario-ingresar" id="usuario-ingresar"
      @click="cerrarMenu"
    >
      <div class="d-block">
        <span class="usuario-close">X</span>
        <h1 class="text-center mb-5 usuario-texto-titulo">
          ¿A qué perfil perteneces?
        </h1>
        <div class="d-flex flex-row">
          <div class="d-flex flex-column align-items-center mx-2 mx-md-5 cursor active-img-logo"
            @click="cambioIndexUsuario('Ciudadania')"
          >
            <img
              src="./assets/img/usuario-ciudadano.png"
              alt="Imagen usuario Ciudadanía"
              class="usuario-icon"
            />
            <span class="usuarios-texto">Ciudadanía</span>
          </div>
          <div class="d-flex flex-column align-items-center mx-2 mx-md-5 cursor"
            @click="cambioIndexUsuario('Servidor')"
          >
            <img
              src="./assets/img/usuario-servidor.png"
              alt="Imagen usuario Servidores"
              class="usuario-icon"
            />
            <span class="usuarios-texto">Servidores</span>
          </div>
        </div>
        <div class="usuario-texto-medellin">
          <h5>
            <center class="font">
              Los cursos y diplomados ofertados en esta plataforma, van
              dirigidos <br />
              exclusivamente a las personas que residan en la ciudad de Medellín
            </center>
          </h5>
        </div>
      </div>
    </div>
    <!-- FIN Home ingreso que desciende -->

    <!-- Visualización de la pantalla completa -->
    <section v-if="index" class="d-block" id="Index">
      <Index />
    </section>
    <section v-if="servidor || ciudadania" id="indexUsuario">
      <IndexUsuario
        :usuario="this.usuario"
        :servidor="this.servidor"
        :ciudadania="this.ciudadania"
      />
    </section>
    <!-- FIN Visualización de la pantalla completa -->
  </div>
</template>

<script>
// Se importan los dos componentes que se van a usar en la página
import Index from './views/ViewIndex.vue'
import IndexUsuario from './views/ViewIndexUsuario.vue'

export default {
  name: 'App',
  data () {
    return {
      index: true,
      servidor: false,
      ciudadania: false,
      usuario: ''
    }
  },
  components: {
    Index,
    IndexUsuario
  },
  methods: {
    cerrarMenu () {
      document.getElementById('usuario-ingresar').style.top = '-150vh'
    },
    cambioIndexUsuario (usuario) {
      this.index = false
      switch (usuario) {
        case 'Ciudadania':
          this.ciudadania = true
          this.usuario = usuario
          break
        case 'Servidor':
          this.servidor = true
          this.usuario = usuario
          break
        default:
          break
      }
    }
  }
}
</script>
