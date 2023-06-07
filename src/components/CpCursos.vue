<template>
  <div>
    <!-- Header -->
    <div>
      <h1 class="mb-5 mt-2 d-flex flex-column index-cursos-titulo-general">
        <div class="d-flex justify-content-between align-items-center">
          <p class="d-flex align-items-center justify-content-center">
            <strong>Cursos</strong>&nbsp; por categoría
          </p>
          <div class="d-flex">
            <input
              class="form-control me-2 d-none d-sm-block"
              id="buscador"
              type="search"
              placeholder="Buscar"
              aria-label="Search"
              v-model="palabraBuscar"
            />
            <button
              id="buttonSearch"
              class="d-block index-cursos-button-search"
              @click="buscarResponsive"
            >
              <span>
                <i class="bi bi-search"></i>
              </span>
              <span>Buscar</span>
            </button>
          </div>
        </div>
        <div class="index-cursos-sub-linea"></div>
      </h1>
    </div>
    <!-- FIN Header -->

    <div v-if="palabraBuscar !== ''">
      <div class="d-flex flex-wrap justify-content-center">
        <CpTarjeta
          :tituloCategoria="'Resultado coincidente'"
          :arrayCategoria="cursos.todosCursos"
          :ciudadania="ciudadania"
          :servidor="servidor"
          :palabraBuscar="palabraBuscar"
        />
      </div>
    </div>
    <!-- FIN Función del buscador -->

    <!-- En caso de que no se este buscando nada, vamos a visualizar lo siguiente -->
    <div v-else>
      <div class="index-cursos-menu">
        <div id="sub-menus" class="d-block h-100 index-cursos-menu-sub">
          <ul class="index-cursos-menu-ul">
            <CpMenuLi
              :arrayNombresCategorias="this.nombresCategorias"
              @cambioCategoria="cambioCategoria"
            />
          </ul>
        </div>

        <div
          id="index-visualizacion"
          class="index-cursos-visualizacion d-none d-md-block"
        >
          <div id="categoria-responsive" class="d-none">
            <label for="">Categoría:</label>
            <select
              class="mx-3 mb-3"
              id="select"
              @change="cambioCategoria($event.target.value, $event.target)"
            >
              <option value="" selected></option>
              <option value="convivencia">
                Convivencia ciudadana
              </option>
              <option value="diversidad">
                Diversidad y género
              </option>
              <option value="gestion">
                Gestión humana
              </option>
              <option value="hacienda">
                Hacienda y contratación
              </option>
              <option value="inclusion">
                Inclusión social
              </option>
              <option value="salud">
                Salud
              </option>
              <option value="vial">
                Seguridad vial
              </option>
              <option value="seguridad">
                Seguridad y salud en el trabajo
              </option>
              <option value="seminarios">
                Seminarios
              </option>
              <option value="social">
                Social
              </option>
              <option value="tecnologia">
                Tecnología e innovación
              </option>
            </select>
          </div>

          <CpTarjeta
            :tituloCategoria="this.tituloCategoria"
            :arrayCategoria="this.arrayCategoria"
            :ciudadania="ciudadania"
            :servidor="servidor"
          />
        </div>
      </div>
    </div>
  </div>
</template>

<script>
import JSONCursos from '../assets/cursos.json'
import CpTarjeta from '../components/CpTarjeta.vue'
import CpMenuLi from '../components/CpMenuLi.vue'

export default {
  name: 'CpCursos',
  data () {
    return {
      cursos: JSONCursos,
      palabraBuscar: '',
      tituloCategoria: 'Recomendado para ti...',
      arrayCategoria: '',
      nombresCategorias: [
        [
          'Convivencia ciudadana',
          'Diversidad y género',
          'Gesión humana',
          'Hacienda y contratación',
          'Inclusión social',
          'Salud',
          'Seguridad vial',
          'Seguridad y salud en el trabajo',
          'Seminarios',
          'Social',
          'Tecnología e innovación'
        ],
        [
          'convivencia',
          'diversidad',
          'gestion',
          'hacienda',
          'inclusion',
          'salud',
          'vial',
          'seguridad',
          'seminarios',
          'social',
          'tecnologia'
        ]
      ]
    }
  },
  props: ['servidor', 'ciudadania'],
  components: {
    CpTarjeta,
    CpMenuLi
  },
  methods: {
    buscarResponsive () {
      if (window.screen.width < 578) {
        const buton = document.getElementById('buttonSearch')
        buton.classList.remove('d-block')
        buton.classList.add('d-none')

        const input = document.getElementById('buscador')
        input.classList.remove('d-none')
        input.classList.add('d-block')
        input.focus()
      }
    },
    cambioCategoria (categoria, categoriaSeleccionada) {
      if (window.screen.width < 768) {
        const menu = document.getElementById('sub-menus')
        menu.classList.remove('d-block')
        menu.classList.add('d-none')

        const menuResponsive = document.getElementById('index-visualizacion')
        menuResponsive.classList.remove('d-none')
        menuResponsive.classList.add('d-block')

        const select = document.getElementById('categoria-responsive')
        select.classList.remove('d-none')
        select.classList.add('d-block')

        this.switch(categoria)
      } else {
        const liCategorias = document.querySelectorAll('.index-cursos-menu-ul-li')
        for (let i = 0; i < liCategorias.length; i++) {
          liCategorias[i].classList.remove('index-cursos-menu-ul-li-activado')
        }
        categoriaSeleccionada.classList.add('index-cursos-menu-ul-li-activado')
        this.switch(categoria)
      }
    },
    switch (categoria) {
      switch (categoria) {
        case 'convivencia':
          this.arrayCategoria = JSONCursos.convivenciaCiudadana
          this.tituloCategoria = 'Convivencia ciudadana'
          break
        case 'diversidad':
          this.arrayCategoria = JSONCursos.diversidadGenero
          this.tituloCategoria = 'Diversidad y género'
          break
        case 'gestion':
          this.arrayCategoria = JSONCursos.gestionHumana
          this.tituloCategoria = 'Gestión humana'
          break
        case 'hacienda':
          this.arrayCategoria = JSONCursos.haciendaContratacion
          this.tituloCategoria = 'Hacienda y contratación'
          break
        case 'inclusion':
          this.arrayCategoria = JSONCursos.inclusionSocial
          this.tituloCategoria = 'Inclusión social'
          break
        case 'salud':
          this.arrayCategoria = JSONCursos.salud
          this.tituloCategoria = 'Salud'
          break
        case 'vial':
          this.arrayCategoria = JSONCursos.seguridadVial
          this.tituloCategoria = 'Seguridad vial'
          break
        case 'seguridad':
          this.arrayCategoria = JSONCursos.seguridadSaludTrabajo
          this.tituloCategoria = 'Seguridad y salud en el trabajo'
          break
        case 'seminarios':
          this.arrayCategoria = JSONCursos.seminarios
          this.tituloCategoria = 'Seminarios'
          break
        case 'social':
          this.arrayCategoria = JSONCursos.social
          this.tituloCategoria = 'Social'
          break
        case 'tecnologia':
          this.arrayCategoria = JSONCursos.tecnologiaInnovacion
          this.tituloCategoria = 'Tecnología e innovación'
          break
        default:
          break
      }
      this.$emit('cambioCategoria', this.tituloCategoria)
    }
  }
}
</script>
