<template>
  <section>
    <div class="d-flex flex-column">
      <div class="mb-3">
        <h3 class="d-flex justify-content-center">
          <span class="index-cursos-titulo">{{tituloCategoria}}</span>
        </h3>
      </div>
      <div class="d-flex flex-row flex-wrap justify-content-center">
        <div
          v-for="curso in arrayCategoria"
          :key="curso.id"
        >
          <div
            class="accordion-item index-cursos-accordion"
            v-if="
            !palabraBuscar &&
            ciudadania &&
            curso.requisitos.ciudadania &&
            curso.requisitos.estado &&
            curso.requisitos.ofertado
            "
          >
            <CpTarjetaContenido
              :id="curso.numeroCurso"
              :src="curso.figure.imagen"
              :alt="curso.figure.alt"
              :titulo="curso.nombre"
              :contenido="curso.contenido"
              :boton="curso.requisitos.botonInscribir"
              :linkBoton="curso.requisitos.link"
              :textoLinkBoton="curso.requisitos.textoLink"
            />
          </div>
          <div
            class="accordion-item index-cursos-accordion"
            v-if="
            !palabraBuscar &&
            servidor &&
            (curso.requisitos.ciudadania || curso.requisitos.servidor) &&
            curso.requisitos.estado &&
            curso.requisitos.ofertado
            "
          >
          <CpTarjetaContenido
            :id="curso.numeroCurso"
            :src="curso.figure.imagen"
            :alt="curso.figure.alt"
            :titulo="curso.nombre"
            :contenido="curso.contenido"
            :boton="curso.requisitos.botonInscribir"
            :linkBoton="curso.requisitos.link"
            :textoLinkBoton="curso.requisitos.textoLink"
          />
          </div>
          <div
            class="accordion-item index-cursos-accordion"
            v-if="
            palabraBuscar &&
            ciudadania &&
            curso.requisitos.ciudadania &&
            curso.requisitos.estado &&
            curso.requisitos.ofertado &&
            (curso.nombre.trim().toLowerCase().indexOf(palabraBuscar.trim().toLowerCase()) !== -1)
            "
          >
          <CpTarjetaContenido
            :id="curso.numeroCurso"
            :src="curso.figure.imagen"
            :alt="curso.figure.alt"
            :titulo="curso.nombre"
            :contenido="curso.contenido"
            :boton="curso.requisitos.botonInscribir"
            :linkBoton="curso.requisitos.link"
            :textoLinkBoton="curso.requisitos.textoLink"
            :categoria="curso.categoria"
          />
          </div>
          <div
            class="accordion-item index-cursos-accordion"
            v-if="
            palabraBuscar &&
            servidor &&
            (curso.requisitos.ciudadania || curso.requisitos.servidor) &&
            curso.requisitos.estado &&
            curso.requisitos.ofertado &&
            (curso.nombre.trim().toLowerCase().indexOf(palabraBuscar.trim().toLowerCase()) !== -1)
            "
          >
          <CpTarjetaContenido
            :id="curso.numeroCurso"
            :src="curso.figure.imagen"
            :alt="curso.figure.alt"
            :titulo="curso.nombre"
            :contenido="curso.contenido"
            :boton="curso.requisitos.botonInscribir"
            :linkBoton="curso.requisitos.link"
            :textoLinkBoton="curso.requisitos.textoLink"
            :categoria="curso.categoria"
          />
          </div>
        </div>
      </div>
    </div>
  </section>
</template>

<script>
import CpTarjetaContenido from '../components/CpTarjetaContenido.vue'

export default {
  name: 'CpTarjeta',
  props: [
    'tituloCategoria',
    'arrayCategoria',
    'ciudadania',
    'servidor',
    'palabraBuscar'
  ],
  components: {
    CpTarjetaContenido
  }
}
</script>
