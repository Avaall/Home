<template>
  <div class="index-nav-usuario">
      <div class="container index-nav-container">
        <div class="d-flex w-50">
          <a href="/" class="index-nav-button-principal">
            <img
              src="../assets/img/index-footer-home.png"
              width="30px"
              height="25px"
              class="fluid"
              alt="Imagen Home"
            />
            <span>Página principal</span>
          </a>
          <span
            @click="cambiarPestana('Cursos')"
            class="index-nav-button"
          >
            Cursos
          </span>
          <span
            @click="cambiarPestana('ConoceMas')"
            class="index-nav-button"
          >
            Conoce más
          </span>
          <span
            @click="cambiarPestana('Cifras')"
            class="index-nav-button"
          >
            Cifras
          </span>
        </div>
        <a href="https://escuelavirtual.medellin.gov.co/campusvirtual/login/index.php"
          target="_blank"
          class="index-nav-button-ingreso"
        >
          Ir al Campus
        </a>
      </div>

      <!-- Navegador responsive para celular o dispositivos pequeños -->
      <div class="index-nav-container-responsive">
        <div class="dropdown">
          <div
            class="index-button-responsive dropdown-toggle"
            data-bs-toggle="dropdown"
            aria-expanded="false"
          >
            <i class="bi bi-list"></i>
          </div>
          <ul class="dropdown-menu">
            <li><a href="/">Página principal</a></li>
            <li @click="cambiarPestana">
              <span class="index-nav-button-responsive">Cursos</span>
            </li>
            <li @click="cambiarPestana">
              <span class="index-nav-button-responsive">Conócenos más</span>
            </li>
          </ul>
        </div>
        <a href="https://escuelavirtual.medellin.gov.co/campusvirtual/login/index.php"
          target="_blank"
          class="index-nav-button-ingreso"
        >
          Ir al Campus
        </a>
      </div>
    </div>
</template>

<script>
export default {
  name: 'CpNavUsuario',
  data () {
    return {
      cursos: false,
      conoceMas: false,
      cifras: false
    }
  },
  methods: {
    cambiarPestana (pestana) {
      switch (pestana) {
        case 'Cursos':
          this.cursos = true
          this.conoceMas = false
          this.cifras = false
          this.$emit('cambiarPestana', pestana, this.cursos, this.conoceMas, this.cifras)
          break
        case 'ConoceMas':
          this.cursos = false
          this.conoceMas = true
          this.cifras = false
          this.$emit('cambiarPestana', 'Conoce más', this.cursos, this.conoceMas, this.cifras)
          break
        case 'Cifras':
          this.cursos = false
          this.conoceMas = false
          this.cifras = true
          this.$emit('cambiarPestana', pestana, this.cursos, this.conoceMas, this.cifras)
          break
        default:
          break
      }
    }
  }
}
</script>
