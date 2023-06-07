<template>
  <div>
    <div v-for="(categoria, posicionCategoria) of arrayNombresCategorias[0]" :key="posicionCategoria">
      <li
        class="index-cursos-menu-ul-li"
        @click="cambioCategoria(arrayNombresCategorias[1][posicionCategoria], $event.target)"
      >
        <i class="bi bi-arrow-right-circle mx-2"></i>
        {{ categoria }}
      </li>
    </div>
  </div>
</template>

<script>
export default {
  name: 'CpMenuLi',
  props: ['arrayNombresCategorias'],
  methods: {
    cambioCategoria (categoria, categoriaSeleccionada) {
      this.$emit('cambioCategoria', categoria, categoriaSeleccionada)
    }
  }
}
</script>
