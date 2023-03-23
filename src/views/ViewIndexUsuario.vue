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

      <!-- Navegador -->
        <div class="index-nav-usuario">

          <!-- Navegador para computadores o dispositivos medianos a grandes -->
            <div class="container index-nav-container">
                <div class="d-flex w-50">
                    <a href="/" class="index-nav-button-principal">
                        <img src="../assets/img/index-footer-home.png" width="30px" height="25px" class="fluid" alt="Imagen Home">
                        <span>Página principal</span>
                    </a>
                  <!-- v-on llama a la función mostrarCursos para visualizar los cursos y ocultar el conoce más -->
                    <span v-on:click="mostrarCursos" class="index-nav-button">Cursos</span>
                  <!-- v-on llama a la función mostrarConoce para visualizar el conóce más y ocultar los cursos -->
                    <span v-on:click="mostrarConoce" class="index-nav-button">Conócenos más</span>
                </div>
                <a href="https://escuelavirtual.medellin.gov.co/login/index.php" target="_blank"
                    class="index-nav-button-ingreso">
                    Ir al Campus
                </a>
            </div>

          <!-- Navegador responsive para celular o dispositivos pequeños -->
            <div class="index-nav-container-responsive">
                <div class="dropdown">
                  <!-- Dentro va la parte visual donde debes de dar click para desplegar el menú -->
                    <div class="index-button-responsive dropdown-toggle" data-bs-toggle="dropdown" aria-expanded="false">
                        <i class="bi bi-list"></i>
                    </div>
                  <!-- Contenido del menú una vez desplegado -->
                    <ul class="dropdown-menu">
                        <li><a href="/">Página principal</a></li>
                      <!-- v-on llama a la función mostrarCursos para visualizar los cursos y ocultar el conoce más -->
                        <li v-on:click="mostrarCursos"><span class="index-nav-button-responsive">Cursos</span></li>
                      <!-- v-on llama a la función mostrarConoce para visualizar el conóce más y ocultar los cursos -->
                        <li v-on:click="mostrarConoce"><span class="index-nav-button-responsive">Conócenos más</span></li>
                    </ul>
                </div>
                <a href="https://escuelavirtual.medellin.gov.co/login/index.php" target="_blank"
                    class="index-nav-button-ingreso">
                    Ir al Campus
                </a>
            </div>

        </div>
      <!-- FIN Navegador -->

      <!-- Visualización del contenido -->
        <div class="container container-b">
            <div v-if="nuevoID == 1" class="mt-3">
                <div id="miga">Ciudadanía > Cursos</div>
            </div>
            <div v-if="nuevoID == 2" class="mt-3">
              <div id="miga2">Servidores > Cursos</div>
          </div>
          <!-- Se crea una condición en la cual solo se visualiza según la variable que este activa como true -->
          <!-- Se le envían 2 props al componente hijo pasando el ID que se viene trayendo desde el padre y el indicadorTecnología que también viene desde el padre -->
            <CpCursos v-if="mostrar_cursos" :indicadorTecnologia="sub_indicadorTecnologia" :ID="sub_id" @cambio="change" />
          <!-- Únicamente tiene la condición para visualizar pero no se necessita envíar ninguna variable -->
            <CpConoceMas v-if="mostrar_conoce" />
        </div>
      <!-- FIN Visualización del contenido -->

      <!-- Footer -->
        <div class="d-flex justify-content-between w-100 home-footer px-0 px-md-5">
          <!-- Izquierda -->
            <div class="d-flex home-footer-limit align-items-center"></div>
          <!-- Centro -->
            <div class="home-footer-limit text-center m-auto">
                <div class="d-flex flex-column justify-content-center mx-3">
                    <span>escuelavirtual@medellin.gov.co</span>
                    <span>(604) 385 5555 Ext. 7398 o 7619</span>
                </div>
            </div>
          <!-- Derecha -->
            <div class="d-flex home-footer-limit">
                <div class="d-flex align-items-center home-footer-limit-2">
                    <img src="../assets/img/footer-logo-sid.png" alt="Logo Secretaría de Innovación Digital" width="90px" class="mx-5 home-footer-img-sid">
                    <img src="../assets/img/footer-logo.png" alt="Logo Alcaldía de Medellín | Distrito de Ciencia, Tecnología e Innovación" width="200px" class="img-fluid home-footer-img">
                </div>
            </div>
        </div>
      <!-- FIN Footer -->

    </div>
</template>

<script>
// Se importan los dos componentes que se van a usar
import CpConoceMas from '../components/CpConoceMas.vue'
import CpCursos from '../components/CpCursos.vue'

export default {
  data () {
    return {
      // mostrar_cursos, sirve para parametrar que se ve en la pantalla, si los cursos o el conoce mas
      mostrar_cursos: true,
      // mostrar_conoce, sirve para parametrar que se ve en la pantalla, si los cursos o el conoce mas
      mostrar_conoce: false,
      // sub_id recibe el ID del usuario, si es ciudadano o servidor
      sub_id: this.nuevoID,
      // sub_indicadorTecnologia recibe una variable que solo se usa en caso de que el cliente de click en el banner para visualizar directamente el curso de Tecnología e Innovación
      sub_indicadorTecnologia: this.indicadorTecnologia
    }
  },
  props: {
    // Se reciben las props que se envían desde el componente padre y se indica el tipo
    nuevoID: {
      type: Number
    },
    indicadorTecnologia: {
      type: Number
    }
  },
  components: {
    CpConoceMas,
    CpCursos
  },
  methods: {
    change (x) {
      if (this.sub_id === 1) {
        if (x === 1) {
          document.getElementById('miga').textContent = 'Ciudadanía > Cursos > Convivencia ciudadana'
        }
        if (x === 2) {
          document.getElementById('miga').textContent = 'Ciudadanía > Cursos > Diversidad y género'
        }
        if (x === 3) {
          document.getElementById('miga').textContent = 'Ciudadanía > Cursos > Gestión humana'
        }
        if (x === 4) {
          document.getElementById('miga').textContent = 'Ciudadanía > Cursos > Hacienda y contratación'
        }
        if (x === 5) {
          document.getElementById('miga').textContent = 'Ciudadanía > Cursos > Inclusión social'
        }
        if (x === 6) {
          document.getElementById('miga').textContent = 'Ciudadanía > Cursos > Salud'
        }
        if (x === 7) {
          document.getElementById('miga').textContent = 'Ciudadanía > Cursos > Seguridad vial'
        }
        if (x === 8) {
          document.getElementById('miga').textContent = 'Ciudadanía > Cursos > Seguridad y salud en el trabajo'
        }
        if (x === 9) {
          document.getElementById('miga').textContent = 'Ciudadanía > Cursos > Seminarios'
        }
        if (x === 10) {
          document.getElementById('miga').textContent = 'Ciudadanía > Cursos > Social'
        }
        if (x === 11) {
          document.getElementById('miga').textContent = 'Ciudadanía > Cursos > Tecnología e innovación'
        }
      }
      if (this.sub_id === 2) {
        if (x === 1) {
          document.getElementById('miga2').textContent = 'Servidores > Cursos > Convivencia ciudadana'
        }
        if (x === 2) {
          document.getElementById('miga2').textContent = 'Servidores > Cursos > Diversidad y género'
        }
        if (x === 3) {
          document.getElementById('miga2').textContent = 'Servidores > Cursos > Gestión humana'
        }
        if (x === 4) {
          document.getElementById('miga2').textContent = 'Servidores > Cursos > Hacienda y contratación'
        }
        if (x === 5) {
          document.getElementById('miga2').textContent = 'Servidores > Cursos > Inclusión social'
        }
        if (x === 6) {
          document.getElementById('miga2').textContent = 'Servidores > Cursos > Salud'
        }
        if (x === 7) {
          document.getElementById('miga2').textContent = 'Servidores > Cursos > Seguridad vial'
        }
        if (x === 8) {
          document.getElementById('miga2').textContent = 'Servidores > Cursos > Seguridad y salud en el trabajo'
        }
        if (x === 9) {
          document.getElementById('miga2').textContent = 'Servidores > Cursos > Seminarios'
        }
        if (x === 10) {
          document.getElementById('miga2').textContent = 'Servidores > Cursos > Social'
        }
        if (x === 11) {
          document.getElementById('miga2').textContent = 'Servidores > Cursos > Tecnología e innovación'
        }
      }
    },
    // Función para visualizar los cursos y ocultar el conoce más
    mostrarCursos () {
      this.mostrar_cursos = true
      this.mostrar_conoce = false
      if (this.sub_id === 1) {
        document.getElementById('miga').textContent = 'Ciudadanía > Cursos'
      }
      if (this.sub_id === 2) {
        document.getElementById('miga2').textContent = 'Servidores > Cursos'
      }
    },
    // Función para visualizar el conoce más y ocultar los cursos
    mostrarConoce () {
      this.mostrar_cursos = false
      this.mostrar_conoce = true
      if (this.sub_id === 1) {
        document.getElementById('miga').textContent = 'Ciudadanía > Conócenos más'
      }
      if (this.sub_id === 2) {
        document.getElementById('miga2').textContent = 'Servidores > Conócenos más'
      }
    }
  }
}
</script>
