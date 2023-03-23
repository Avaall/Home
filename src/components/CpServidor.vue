<template>
    <div>
        <div>
            <!-- 0 -->
            <div v-if="propt == 0" class="text-center index-cursos-ciudadano-portada-2">
                <div class="index-cursos-ciudadano-categoria">
                    <p><strong>¡Hola!</strong> esta es la oferta <br> de cursos para <strong> Servidores </strong> </p>
                </div>
            </div>
            <!-- 1 -->
            <div v-if="propt == 1" class="d-flex flex-column">
                <div class="mb-3">
                    <h3 class="d-flex justify-content-center">
                        <span class="index-cursos-titulo">Convivencia ciudadana</span>
                    </h3>
                </div>
                <div class="d-flex flex-row flex-wrap justify-content-center">
                    <div v-for="(cursoConvivenciaCiudadana, identificador) in cursos.convivenciaCiudadana" :key="cursoConvivenciaCiudadana.id">
                        <div v-if="cursoConvivenciaCiudadana.requisitos.estado == 'activo' && cursoConvivenciaCiudadana.requisitos.ofertado == 'si' && (cursoConvivenciaCiudadana.requisitos.usuario == 1 || cursoConvivenciaCiudadana.requisitos.usuario == 2)" class="accordion-item index-cursos-accordion">
                            <h2 class="accordion-header" v-on:click="cambio(cursoConvivenciaCiudadana.numeroCurso)">
                                <button class="index-cursos-accordion-button" type="button" data-bs-toggle="collapse" :data-bs-target="'#'+identificador" aria-expanded="false" :aria-controls="identificador">
                                    <img :src="cursoConvivenciaCiudadana.figure.imagen" :alt="cursoConvivenciaCiudadana.figure.alt" class="rounded img-img" width="300px">
                                    <p class="index-cursos-titulo-accordion">
                                        <strong>{{ cursoConvivenciaCiudadana.nombre }}</strong>
                                    </p>
                                    <span>
                                        <div :class="cursoConvivenciaCiudadana.numeroCurso">Conoce Más</div>&nbsp;
                                        <i :class="'bi bi-caret-down-fill ' + cursoConvivenciaCiudadana.numeroCurso"></i>
                                    </span>
                                </button>
                            </h2>
                            <div :id="identificador" class="collapse" aria-labelledby="acordion1" data-bs-parent="#home-accordion">
                                <div class="index-cursos-cuerpo-accordion">
                                    <div class="d-flex align-items-center">
                                        {{ cursoConvivenciaCiudadana.contenido }}
                                    </div>
                                    <div v-if="cursoConvivenciaCiudadana.requisitos.botonInscribir == 'si'" class="d-flex justify-content-center">
                                        <a :href="cursoConvivenciaCiudadana.requisitos.link" class="index-cursos-button-inscribete" target="_blank">INSCRIBETE</a>
                                    </div>
                                </div>
                            </div>
                        </div>
                    </div>
                </div>
            </div>
            <!-- 2 -->
            <div v-if="propt == 2" class="d-flex flex-column">
                <div class="mb-3">
                    <h3 class="d-flex justify-content-center">
                        <span class="index-cursos-titulo">Diversidad y género</span>
                    </h3>
                </div>
                <div class="d-flex flex-wrap justify-content-center">
                    <div v-for="(cursodiversidadGenero, identificador) in cursos.diversidadGenero" :key="cursodiversidadGenero.id">
                        <div v-if="cursodiversidadGenero.requisitos.estado == 'activo' && cursodiversidadGenero.requisitos.ofertado == 'si' && (cursodiversidadGenero.requisitos.usuario == 1 || cursodiversidadGenero.requisitos.usuario == 2)" class="accordion-item index-cursos-accordion">
                            <h2 class="accordion-header" v-on:click="cambio(cursodiversidadGenero.numeroCurso)">
                                <button class="index-cursos-accordion-button" type="button" data-bs-toggle="collapse" :data-bs-target="'#'+identificador" aria-expanded="false" :aria-controls="identificador">
                                    <img :src="cursodiversidadGenero.figure.imagen" :alt="cursodiversidadGenero.figure.alt" class="rounded img-img" width="300px">
                                    <p class="index-cursos-titulo-accordion">
                                        <strong>{{ cursodiversidadGenero.nombre }}</strong>
                                    </p>
                                    <span>
                                        <div :class="cursodiversidadGenero.numeroCurso">Conoce Más</div>&nbsp;
                                        <i :class="'bi bi-caret-down-fill ' + cursodiversidadGenero.numeroCurso"></i>
                                    </span>
                                </button>
                            </h2>
                            <div :id="identificador" class="collapse" aria-labelledby="acordion1" data-bs-parent="#home-accordion">
                                <div class="index-cursos-cuerpo-accordion">
                                    <div class="d-flex align-items-center">
                                        {{ cursodiversidadGenero.contenido }}
                                    </div>
                                    <div v-if="cursodiversidadGenero.requisitos.botonInscribir == 'si'" class="d-flex justify-content-center">
                                        <a :href="cursodiversidadGenero.requisitos.link" class="index-cursos-button-inscribete" target="_blank">INSCRIBETE</a>
                                    </div>
                                </div>
                            </div>
                        </div>
                    </div>
                </div>
            </div>
            <!-- 3 -->
            <div v-if="propt == 3" class="d-flex flex-column">
                <div class="mb-3">
                    <h3 class="d-flex justify-content-center">
                        <span class="index-cursos-titulo">Gestión humana</span>
                    </h3>
                </div>
                <div class="d-flex flex-wrap justify-content-center">
                    <div v-for="(cursogestionHumana, identificador) in cursos.gestionHumana" :key="cursogestionHumana.id">
                        <div v-if="cursogestionHumana.requisitos.estado == 'activo' && cursogestionHumana.requisitos.ofertado == 'si' && (cursogestionHumana.requisitos.usuario == 1 || cursogestionHumana.requisitos.usuario == 2)" class="accordion-item index-cursos-accordion">
                            <h2 class="accordion-header" v-on:click="cambio(cursogestionHumana.numeroCurso)">
                                <button class="index-cursos-accordion-button" type="button" data-bs-toggle="collapse" :data-bs-target="'#'+identificador" aria-expanded="false" :aria-controls="identificador">
                                    <img :src="cursogestionHumana.figure.imagen" :alt="cursogestionHumana.figure.alt" class="rounded img-img" width="300px">
                                    <p class="index-cursos-titulo-accordion">
                                        <strong>{{ cursogestionHumana.nombre }}</strong>
                                    </p>
                                    <span>
                                        <div :class="cursogestionHumana.numeroCurso">Conoce Más</div>&nbsp;
                                        <i :class="'bi bi-caret-down-fill ' + cursogestionHumana.numeroCurso"></i>
                                    </span>
                                </button>
                            </h2>
                            <div :id="identificador" class="collapse" aria-labelledby="acordion1" data-bs-parent="#home-accordion">
                                <div class="index-cursos-cuerpo-accordion">
                                    <div class="d-flex align-items-center">
                                        {{ cursogestionHumana.contenido }}
                                    </div>
                                    <div v-if="cursogestionHumana.requisitos.botonInscribir == 'si'" class="d-flex justify-content-center">
                                        <a :href="cursogestionHumana.requisitos.link" class="index-cursos-button-inscribete" target="_blank">INSCRIBETE</a>
                                    </div>
                                </div>
                            </div>
                        </div>
                    </div>
                </div>
            </div>
            <!-- 4 -->
            <div v-if="propt == 4" class="d-flex flex-column">
                <div class="mb-3">
                    <h3 class="d-flex justify-content-center">
                        <span class="index-cursos-titulo">Hacienda y contratación</span>
                    </h3>
                </div>
                <div class="d-flex flex-wrap justify-content-center">
                    <div v-for="(cursohaciendaContratacion, identificador) in cursos.haciendaContratacion" :key="cursohaciendaContratacion.id">
                        <div v-if="cursohaciendaContratacion.requisitos.estado == 'activo' && cursohaciendaContratacion.requisitos.ofertado == 'si' && (cursohaciendaContratacion.requisitos.usuario == 1 || cursohaciendaContratacion.requisitos.usuario == 2)" class="accordion-item index-cursos-accordion">
                            <h2 class="accordion-header" v-on:click="cambio(cursohaciendaContratacion.numeroCurso)">
                                <button class="index-cursos-accordion-button" type="button" data-bs-toggle="collapse" :data-bs-target="'#'+identificador" aria-expanded="false" :aria-controls="identificador">
                                    <img :src="cursohaciendaContratacion.figure.imagen" :alt="cursohaciendaContratacion.figure.alt" class="rounded img-img" width="300px">
                                    <p class="index-cursos-titulo-accordion">
                                        <strong>{{ cursohaciendaContratacion.nombre }}</strong>
                                    </p>
                                    <span>
                                        <div :class="cursohaciendaContratacion.numeroCurso">Conoce Más</div>&nbsp;
                                        <i :class="'bi bi-caret-down-fill ' + cursohaciendaContratacion.numeroCurso"></i>
                                    </span>
                                </button>
                            </h2>
                            <div :id="identificador" class="collapse" aria-labelledby="acordion1" data-bs-parent="#home-accordion">
                                <div class="index-cursos-cuerpo-accordion">
                                    <div class="d-flex align-items-center">
                                        {{ cursohaciendaContratacion.contenido }}
                                    </div>
                                    <div v-if="cursohaciendaContratacion.requisitos.botonInscribir == 'si'" class="d-flex justify-content-center">
                                        <a :href="cursohaciendaContratacion.requisitos.link" class="index-cursos-button-inscribete" target="_blank">INSCRIBETE</a>
                                    </div>
                                </div>
                            </div>
                        </div>
                    </div>
                </div>
            </div>
            <!-- 5 -->
            <div v-if="propt == 5" class="d-flex flex-column">
                <div class="mb-3">
                    <h3 class="d-flex justify-content-center">
                        <span class="index-cursos-titulo">Inclusión social</span>
                    </h3>
                </div>
                <div class="d-flex flex-wrap justify-content-center">
                    <div v-for="(cursoinclusionSocial, identificador) in cursos.inclusionSocial" :key="cursoinclusionSocial.id">
                        <div v-if="cursoinclusionSocial.requisitos.estado == 'activo' && cursoinclusionSocial.requisitos.ofertado == 'si' && (cursoinclusionSocial.requisitos.usuario == 1 || cursoinclusionSocial.requisitos.usuario == 2)" class="accordion-item index-cursos-accordion">
                            <h2 class="accordion-header" v-on:click="cambio(cursoinclusionSocial.numeroCurso)">
                                <button class="index-cursos-accordion-button" type="button" data-bs-toggle="collapse" :data-bs-target="'#'+identificador" aria-expanded="false" :aria-controls="identificador">
                                    <img :src="cursoinclusionSocial.figure.imagen" :alt="cursoinclusionSocial.figure.alt" class="rounded img-img" width="300px">
                                    <p class="index-cursos-titulo-accordion">
                                        <strong>{{ cursoinclusionSocial.nombre }}</strong>
                                    </p>
                                    <span>
                                        <div :class="cursoinclusionSocial.numeroCurso">Conoce Más</div>&nbsp;
                                        <i :class="'bi bi-caret-down-fill ' + cursoinclusionSocial.numeroCurso"></i>
                                    </span>
                                </button>
                            </h2>
                            <div :id="identificador" class="collapse" aria-labelledby="acordion1" data-bs-parent="#home-accordion">
                                <div class="index-cursos-cuerpo-accordion">
                                    <div class="d-flex align-items-center">
                                        {{ cursoinclusionSocial.contenido }}
                                    </div>
                                    <div v-if="cursoinclusionSocial.requisitos.botonInscribir == 'si'" class="d-flex justify-content-center">
                                        <a :href="cursoinclusionSocial.requisitos.link" class="index-cursos-button-inscribete" target="_blank">INSCRIBETE</a>
                                    </div>
                                </div>
                            </div>
                        </div>
                    </div>
                </div>
            </div>
            <!-- 6 -->
            <div v-if="propt == 6" class="d-flex flex-column">
                <div class="mb-3">
                    <h3 class="d-flex justify-content-center">
                        <span class="index-cursos-titulo">Salud</span>
                    </h3>
                </div>
                <div class="d-flex flex-wrap justify-content-center">
                    <div v-for="(cursosalud, identificador) in cursos.salud" :key="cursosalud.id">
                        <div v-if="cursosalud.requisitos.estado == 'activo' && cursosalud.requisitos.ofertado == 'si' && (cursosalud.requisitos.usuario == 1 || cursosalud.requisitos.usuario == 2)" class="accordion-item index-cursos-accordion">
                            <h2 class="accordion-header" v-on:click="cambio(cursosalud.numeroCurso)">
                                <button class="index-cursos-accordion-button" type="button" data-bs-toggle="collapse" :data-bs-target="'#'+identificador" aria-expanded="false" :aria-controls="identificador">
                                    <img :src="cursosalud.figure.imagen" :alt="cursosalud.figure.alt" class="rounded img-img" width="300px">
                                    <p class="index-cursos-titulo-accordion">
                                        <strong>{{ cursosalud.nombre }}</strong>
                                    </p>
                                    <span>
                                        <div :class="cursosalud.numeroCurso">Conoce Más</div>&nbsp;
                                        <i :class="'bi bi-caret-down-fill ' + cursosalud.numeroCurso"></i>
                                    </span>
                                </button>
                            </h2>
                            <div :id="identificador" class="collapse" aria-labelledby="acordion1" data-bs-parent="#home-accordion">
                                <div class="index-cursos-cuerpo-accordion">
                                    <div class="d-flex align-items-center">
                                        {{ cursosalud.contenido }}
                                    </div>
                                    <div v-if="cursosalud.requisitos.botonInscribir == 'si'" class="d-flex justify-content-center">
                                        <a :href="cursosalud.requisitos.link" class="index-cursos-button-inscribete" target="_blank">INSCRIBETE</a>
                                    </div>
                                </div>
                            </div>
                        </div>
                    </div>
                </div>
            </div>
            <!-- 7 -->
            <div v-if="propt == 7" class="d-flex flex-column">
                <div class="mb-3">
                    <h3 class="d-flex justify-content-center">
                        <span class="index-cursos-titulo">Seguridad vial</span>
                    </h3>
                </div>
                <div class="d-flex flex-wrap justify-content-center">
                    <div v-for="(cursoseguridadVial, identificador) in cursos.seguridadVial" :key="cursoseguridadVial.id">
                        <div v-if="cursoseguridadVial.requisitos.estado == 'activo' && cursoseguridadVial.requisitos.ofertado == 'si' && (cursoseguridadVial.requisitos.usuario == 1 || cursoseguridadVial.requisitos.usuario == 2)" class="accordion-item index-cursos-accordion">
                            <h2 class="accordion-header" v-on:click="cambio(cursoseguridadVial.numeroCurso)">
                                <button class="index-cursos-accordion-button" type="button" data-bs-toggle="collapse" :data-bs-target="'#'+identificador" aria-expanded="false" :aria-controls="identificador">
                                    <img :src="cursoseguridadVial.figure.imagen" :alt="cursoseguridadVial.figure.alt" class="rounded img-img" width="300px">
                                    <p class="index-cursos-titulo-accordion">
                                        <strong>{{ cursoseguridadVial.nombre }}</strong>
                                    </p>
                                    <span>
                                        <div :class="cursoseguridadVial.numeroCurso">Conoce Más</div>&nbsp;
                                        <i :class="'bi bi-caret-down-fill ' + cursoseguridadVial.numeroCurso"></i>
                                    </span>
                                </button>
                            </h2>
                            <div :id="identificador" class="collapse" aria-labelledby="acordion1" data-bs-parent="#home-accordion">
                                <div class="index-cursos-cuerpo-accordion">
                                    <div class="d-flex align-items-center">
                                        {{ cursoseguridadVial.contenido }}
                                    </div>
                                    <div v-if="cursoseguridadVial.requisitos.botonInscribir == 'si'" class="d-flex justify-content-center">
                                        <a :href="cursoseguridadVial.requisitos.link" class="index-cursos-button-inscribete" target="_blank">INSCRIBETE</a>
                                    </div>
                                </div>
                            </div>
                        </div>
                    </div>
                </div>
            </div>
            <!-- 8 -->
            <div v-if="propt == 8" class="d-flex flex-column">
                <div class="mb-3">
                    <h3 class="d-flex justify-content-center">
                        <span class="index-cursos-titulo">Seguridad y salud en el trabajo</span>
                    </h3>
                </div>
                <div class="d-flex flex-wrap justify-content-center">
                    <div v-for="(cursoseguridadSaludTrabajo, identificador) in cursos.seguridadSaludTrabajo" :key="cursoseguridadSaludTrabajo.id">
                        <div v-if="cursoseguridadSaludTrabajo.requisitos.estado == 'activo' && cursoseguridadSaludTrabajo.requisitos.ofertado == 'si' && (cursoseguridadSaludTrabajo.requisitos.usuario == 1 || cursoseguridadSaludTrabajo.requisitos.usuario == 2)" class="accordion-item index-cursos-accordion">
                            <h2 class="accordion-header" v-on:click="cambio(cursoseguridadSaludTrabajo.numeroCurso)">
                                <button class="index-cursos-accordion-button" type="button" data-bs-toggle="collapse" :data-bs-target="'#'+identificador" aria-expanded="false" :aria-controls="identificador">
                                    <img :src="cursoseguridadSaludTrabajo.figure.imagen" :alt="cursoseguridadSaludTrabajo.figure.alt" class="rounded img-img" width="300px">
                                    <p class="index-cursos-titulo-accordion">
                                        <strong>{{ cursoseguridadSaludTrabajo.nombre }}</strong>
                                    </p>
                                    <span>
                                        <div :class="cursoseguridadSaludTrabajo.numeroCurso">Conoce Más</div>&nbsp;
                                        <i :class="'bi bi-caret-down-fill ' + cursoseguridadSaludTrabajo.numeroCurso"></i>
                                    </span>
                                </button>
                            </h2>
                            <div :id="identificador" class="collapse" aria-labelledby="acordion1" data-bs-parent="#home-accordion">
                                <div class="index-cursos-cuerpo-accordion">
                                    <div class="d-flex align-items-center">
                                        {{ cursoseguridadSaludTrabajo.contenido }}
                                    </div>
                                    <div v-if="cursoseguridadSaludTrabajo.requisitos.botonInscribir == 'si'" class="d-flex justify-content-center">
                                        <a :href="cursoseguridadSaludTrabajo.link" class="index-cursos-button-inscribete" target="_blank">INSCRIBETE</a>
                                    </div>
                                </div>
                            </div>
                        </div>
                    </div>
                </div>
            </div>
            <!-- 9 -->
            <div v-if="propt == 9" class="d-flex flex-column">
                <div class="mb-3">
                    <h3 class="d-flex justify-content-center">
                        <span class="index-cursos-titulo">Seminarios</span>
                    </h3>
                </div>
                <div class="d-flex flex-wrap justify-content-center">
                    <div v-for="(cursoseminarios, identificador) in cursos.seminarios" :key="cursoseminarios.id">
                        <div v-if="cursoseminarios.requisitos.estado == 'activo' && cursoseminarios.requisitos.ofertado == 'si' && (cursoseminarios.requisitos.usuario == 1 || cursoseminarios.requisitos.usuario == 2)" class="accordion-item index-cursos-accordion">
                            <h2 class="accordion-header" v-on:click="cambio(cursoseminarios.numeroCurso)">
                                <button class="index-cursos-accordion-button" type="button" data-bs-toggle="collapse" :data-bs-target="'#'+identificador" aria-expanded="false" :aria-controls="identificador">
                                    <img :src="cursoseminarios.figure.imagen" :alt="cursoseminarios.figure.alt" class="rounded img-img" width="300px">
                                    <p class="index-cursos-titulo-accordion">
                                        <strong>{{ cursoseminarios.nombre }}</strong>
                                    </p>
                                    <span>
                                        <div :class="cursoseminarios.numeroCurso">Conoce Más</div>&nbsp;
                                        <i :class="'bi bi-caret-down-fill ' + cursoseminarios.numeroCurso"></i>
                                    </span>
                                </button>
                            </h2>
                            <div :id="identificador" class="collapse" aria-labelledby="acordion1" data-bs-parent="#home-accordion">
                                <div class="index-cursos-cuerpo-accordion">
                                    <div class="d-flex align-items-center">
                                        {{ cursoseminarios.contenido }}
                                    </div>
                                    <div v-if="cursoseminarios.requisitos.botonInscribir == 'si'" class="d-flex justify-content-center">
                                        <a :href="cursoseminarios.requisitos.link" class="index-cursos-button-inscribete" target="_blank">INSCRIBETE</a>
                                    </div>
                                </div>
                            </div>
                        </div>
                    </div>
                </div>
            </div>
            <!-- 10 -->
            <div v-if="propt == 10" class="d-flex flex-column">
                <div class="mb-3">
                    <h3 class="d-flex justify-content-center">
                        <span class="index-cursos-titulo">Social</span>
                    </h3>
                </div>
                <div class="d-flex flex-wrap justify-content-center">
                    <div v-for="(cursosocial, identificador) in cursos.social" :key="cursosocial.id">
                        <div v-if="cursosocial.requisitos.estado == 'activo' && cursosocial.requisitos.ofertado == 'si' && (cursosocial.requisitos.usuario == 1 || cursosocial.requisitos.usuario == 2)" class="accordion-item index-cursos-accordion">
                            <h2 class="accordion-header" v-on:click="cambio(cursosocial.numeroCurso)">
                                <button class="index-cursos-accordion-button" type="button" data-bs-toggle="collapse" :data-bs-target="'#'+identificador" aria-expanded="false" :aria-controls="identificador">
                                    <img :src="cursosocial.figure.imagen" :alt="cursosocial.figure.alt" class="rounded img-img" width="300px">
                                    <p class="index-cursos-titulo-accordion">
                                        <strong>{{ cursosocial.nombre }}</strong>
                                    </p>
                                    <span>
                                        <div :class="cursosocial.numeroCurso">Conoce Más</div>&nbsp;
                                        <i :class="'bi bi-caret-down-fill ' + cursosocial.numeroCurso"></i>
                                    </span>
                                </button>
                            </h2>
                            <div :id="identificador" class="collapse" aria-labelledby="acordion1" data-bs-parent="#home-accordion">
                                <div class="index-cursos-cuerpo-accordion">
                                    <div class="d-flex align-items-center">
                                        {{ cursosocial.contenido }}
                                    </div>
                                    <div v-if="cursosocial.requisitos.botonInscribir == 'si'" class="d-flex justify-content-center">
                                        <a :href="cursosocial.requisitos.link" class="index-cursos-button-inscribete" target="_blank">INSCRIBETE</a>
                                    </div>
                                </div>
                            </div>
                        </div>
                    </div>
                </div>
            </div>
            <!-- 11 -->
            <div v-if="propt == 11" class="d-flex flex-column">
                <div class="mb-3">
                    <h3 class="d-flex justify-content-center">
                        <span class="index-cursos-titulo">Tecnología e innovación</span>
                    </h3>
                </div>
                <div class="d-flex flex-wrap justify-content-center">
                    <div v-for="(cursotecnologiaInnovacion, identificador) in cursos.tecnologiaInnovacion" :key="cursotecnologiaInnovacion.id">
                        <div v-if="cursotecnologiaInnovacion.requisitos.estado == 'activo' && cursotecnologiaInnovacion.requisitos.ofertado == 'si' && (cursotecnologiaInnovacion.requisitos.usuario == 1 || cursotecnologiaInnovacion.requisitos.usuario == 2)" class="accordion-item index-cursos-accordion">
                            <h2 class="accordion-header" v-on:click="cambio(cursotecnologiaInnovacion.numeroCurso)">
                                <button class="index-cursos-accordion-button" type="button" data-bs-toggle="collapse" :data-bs-target="'#'+identificador" aria-expanded="false" :aria-controls="identificador">
                                    <img :src="cursotecnologiaInnovacion.figure.imagen" :alt="cursotecnologiaInnovacion.figure.alt" class="rounded img-img" width="300px">
                                    <p class="index-cursos-titulo-accordion">
                                        <strong>{{ cursotecnologiaInnovacion.nombre }}</strong>
                                    </p>
                                    <span>
                                        <div :class="cursotecnologiaInnovacion.numeroCurso">Conoce Más</div>&nbsp;
                                        <i :class="'bi bi-caret-down-fill ' + cursotecnologiaInnovacion.numeroCurso"></i>
                                    </span>
                                </button>
                            </h2>
                            <div :id="identificador" class="collapse" aria-labelledby="acordion1" data-bs-parent="#home-accordion">
                                <div class="index-cursos-cuerpo-accordion">
                                    <div class="d-flex align-items-center">
                                        {{ cursotecnologiaInnovacion.contenido }}
                                    </div>
                                    <div v-if="cursotecnologiaInnovacion.requisitos.botonInscribir == 'si'" class="d-flex justify-content-center">
                                        <a :href="cursotecnologiaInnovacion.requisitos.link" class="index-cursos-button-inscribete" target="_blank">INSCRIBETE</a>
                                    </div>
                                </div>
                            </div>
                        </div>
                    </div>
                </div>
            </div>
        </div>
    </div>
</template>

<script>
import datos from '../assets/cursos.json'

export default {
  name: 'CpServidor',
  data () {
    return {
      cursos: datos
    }
  },
  props: {
    propt: {
      type: Number
    }
  },
  methods: {
    cambio (id) {
      const indice = document.querySelectorAll('.' + id)
      if (indice[0].textContent === 'Conoce Más') {
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
