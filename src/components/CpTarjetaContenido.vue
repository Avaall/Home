<template>
  <div>
    <h2 class="accordion-header">
      <button
        class="index-cursos-accordion-button"
        type="button"
        data-bs-toggle="collapse"
        aria-expanded="true"
        :aria-controls="id"
        :data-bs-target="'#' + id"
        @click="verMas(id)"
      >
        <img
          :src="src"
          :alt="alt"
          class="rounded img-img"
          width="300px"
        />
        <p class="index-cursos-titulo-accordion">
          <strong>{{titulo}}</strong><br>
          <i style="font-size: 14px">{{categoria}}</i>
        </p>
        <span>
          <div :class="id">
            Conoce Más
          </div>&nbsp;
          <i :class="'bi bi-caret-down-fill ' + id"></i>
        </span>
      </button>
    </h2>
    <div
      :id="id"
      class="collapse"
    >
      <div class="index-cursos-cuerpo-accordion">
        <div class="d-flex align-items-center">
          {{contenido}}
        </div>
        <div
          class="d-flex justify-content-center"
          v-if="boton"
        >
          <a
            :href="linkBoton"
            class="index-cursos-button-inscribete"
            target="_blank"
          >
            {{textoLinkBoton}}
          </a>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: 'CpTarjetaContenido',
  props: [
    'id',
    'src',
    'alt',
    'titulo',
    'contenido',
    'boton',
    'linkBoton',
    'textoLinkBoton',
    'categoria'
  ],
  methods: {
    verMas (id) {
      const indice = document.querySelectorAll('.' + id)
      if (indice[0].textContent !== 'Ocultar') {
        indice[0].textContent = 'Ocultar'
        indice[1].style.transition = '.3s'
        indice[1].style.transform = 'rotate(180deg)'
      } else {
        indice[0].textContent = 'Conoce Más'
        indice[1].style.transition = '.3s'
        indice[1].style.transform = 'rotate(0deg)'
      }
    }
  }
}
</script>
