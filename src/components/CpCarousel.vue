<template>
  <div id="carousel" class="carousel slide home-carousel" data-bs-ride="true">
      <!-- Indicadores de cuantas páginas tiene el banner -->
      <div class="carousel-indicators">
        <button
          type="button"
          data-bs-target="#carousel"
          data-bs-slide-to="0"
          class="active"
          aria-current="true"
          aria-label="Slide 1"
        ></button>
        <button
          type="button"
          data-bs-target="#carousel"
          data-bs-slide-to="1"
          aria-label="Slide 2"
        ></button>
        <button
          type="button"
          data-bs-target="#carousel"
          data-bs-slide-to="2"
          aria-label="Slide 3"
        ></button>
      </div>
      <!-- Acá se reposita cada uno de los items o páginas del carousel, debe de coincidir con la cantidad de indicadores de pestañas para evitar bugs -->
      <div class="carousel-inner">
        <!-- Primer banner -->
        <div class="carousel-item carousel-item-unic active">
          <div class="carousel-caption h-100"></div>
        </div>
        <!-- Segundo banner -->
        <div class="carousel-item carousel-item-unic-2">
          <div
            class="carousel-caption d-flex justify-content-center justify-content-sm-end h-100 align-items-center home-carousel-animation"
          >
            <img
              src="../assets/img/carousel-logo-escuela.png"
              alt="Imagen logo Escuela Virtual de Aprendizaje"
              class="img-info-caption info-caption"
            />
          </div>
        </div>
        <!-- Tercer banner -->
        <div class="carousel-item carousel-item-unic-3">
          <div
            class="carousel-caption d-flex flex-column justify-content-center h-100 align-items-center"
          >
            <div class="home-carousel-text home-carousel-animation">
              <center class="info-caption-text">
                <span
                  >La <strong>Escuela Virtual de Aprendizaje</strong><br />es un
                  espacio para compartir,<br />
                  explorar y descubrir conocimientos</span
                >
              </center>
            </div>
          </div>
        </div>
      </div>
      <!-- Botones para avanzar y volver entre items -->
      <button
        class="carousel-control-prev"
        type="button"
        data-bs-target="#carousel"
        data-bs-slide="prev"
      >
        <span class="carousel-control-prev-icon" aria-hidden="true"></span>
        <span class="visually-hidden">Previous</span>
      </button>
      <button
        class="carousel-control-next"
        type="button"
        data-bs-target="#carousel"
        data-bs-slide="next"
      >
        <span class="carousel-control-next-icon" aria-hidden="true"></span>
        <span class="visually-hidden">Next</span>
      </button>
    </div>
</template>

<script>
export default {
  name: 'CpCarousel'
}
</script>
