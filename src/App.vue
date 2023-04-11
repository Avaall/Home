<template>
    <div id="app">
      <div v-if="isLoading">
        Hola
      </div>
      <div v-if="!isLoading">
      <!-- Home ingreso que desciende -->
        <div class="position-fixed usuario-ingresar" id="usuario-ingresar" v-on:click="CerrarMenu">
            <div class="d-block">
                <span class="usuario-close">X</span>
                <h1 class="text-center mb-5 usuario-texto-titulo">¿A qué perfil perteneces?</h1>
                <div class="d-flex flex-row">
                  <!-- v-on llama la función cambiarValor y lleva el indicador del usuario -->
                    <div v-on:click="cambiarValor(1)" class="d-flex flex-column align-items-center mx-2 mx-md-5 cursor active-img-logo">
                        <img src="./assets/img/usuario-ciudadano.png" alt="Imagen usuario Ciudadanía" height="215px" class="usuario-icon">
                        <span class="usuarios-texto">Ciudadanía</span>
                    </div>
                  <!-- v-on llama la función cambiarValor y lleva el indicador del usuario -->
                    <div v-on:click="cambiarValor(2)" class="d-flex flex-column align-items-center mx-2 mx-md-5 cursor">
                        <img src="./assets/img/usuario-servidor.png" alt="Imagen usuario Servidores" height="215px" class="usuario-icon">
                        <span class="usuarios-texto">Servidores</span>
                    </div>
                </div>
                <div class="usuario-texto-medellin">
                    <h5>
                      <center class="font">
                        Los cursos y diplomados ofertados en esta plataforma, van dirigidos <br>
                        exclusivamente a las personas que residan en la ciudad de Medellín
                      </center>
                    </h5>
                </div>
            </div>
        </div>
      <!-- FIN Home ingreso que desciende -->

      <!-- Visualización de la pantalla completa -->
        <section v-if="mostrarIndexUsuario" id="indexUsuario">
          <!-- Se envían 2 variables al componente hijo, el ID del usuario y el indicador por si esta interesado en tecnología -->
            <IndexUsuario :nuevoID="nuevoID" :indicadorTecnologia="indicadorTecnologia" />
        </section>
        <section v-else class="d-block" id="Index">
          <!-- Se recibe la función cambiarValor de parte del hijo para que se pueda pasar automaticamente a la categoría de Tecnología e Innovación -->
            <Index @cambiarValor="cambiarValor (3)" />
        </section>
      <!-- FIN Visualización de la pantalla completa -->
      </div>
    </div>
</template>

<script>
// Se importan los dos componentes que se van a usar en la página
import Index from './views/ViewIndex.vue'
import IndexUsuario from './views/ViewIndexUsuario.vue'

export default {
  data () {
    return {
      // mostrarIndex usuario sirve para indicar que va a visualizar el usuario
      mostrarIndexUsuario: false,
      // nuevoID se refiere al usuario, 1 = ciudadano, 2 = servidor
      nuevoID: 0,
      // indicadorTecnologia es una variable que solo se usa cuando le das click al banner para ir directo a la categoría tecnología
      indicadorTecnologia: 0,
      isLoading: true
    }
  },
  name: 'App',
  components: {
    Index,
    IndexUsuario
  },
  mounted () {
    window.addEventListener('load', () => {
      this.isLoading = false
    })
  },
  methods: {
    // Función que cierra el menú
    CerrarMenu () {
      document.getElementById('usuario-ingresar').style.top = '-150vh'
    },
    // Función que identifica que usuario se va a ingresar y visualiza según sea
    cambiarValor (x) {
      if (x === 1) {
        this.mostrarIndexUsuario = true
        this.nuevoID = 1
      }
      if (x === 2) {
        this.mostrarIndexUsuario = true
        this.nuevoID = 2
      }
      if (x === 3) {
        this.mostrarIndexUsuario = true
        this.nuevoID = 1
        this.indicadorTecnologia = 11
      }
    }
  }
}
</script>
