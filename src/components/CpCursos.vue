<template>
    <div>

        <!-- Header -->
        <div>
            <h1 class="mb-5 mt-2 d-flex flex-column index-cursos-titulo-general">
                <div class="d-flex justify-content-between align-items-center">
                    <p class="d-flex align-items-center justify-content-center"><strong>Cursos</strong>&nbsp;por categoría</p>
                    <!-- Buscador visual, caja de texto y botón -->
                    <div class="d-flex">
                        <!-- Esta enlazado con la variable buscar que se define en los scripts -->
                        <input class="form-control me-2 d-none d-sm-block" id="buscador" type="search" placeholder="Buscar" v-model="buscar" aria-label="Search">
                        <!-- Maneja una variable que solo se activa si esta en versión responsive -->
                        <button id="buttonSearch" class="d-block index-cursos-button-search" v-on:click="buscarResponsive">
                            <!-- Cambia entre una lupa y el texto buscar para versión de celulares o dispositivos similares -->
                            <span>
                                <i class="bi bi-search"></i>
                            </span>
                            <span>Buscar</span>
                        </button>
                    </div>
                </div>
                <!-- Unicamente es la linea divisora -->
                <div class="index-cursos-sub-linea"></div>
            </h1>
        </div>
        <!-- FIN Header -->

        <!-- Función de buscador -->
        <!-- Cada una de las 'cartas' que se visualiza cuando buscas, tiene condiciones que cumplir y se muestran en forma de accordion -->
        <!-- Se usa una condición de que solo se visualice cuando se este buscando algo en el momento -->
        <div v-if="buscar !== ''">
            <div class="d-none">{{ this.numeroCategoria = 0 }}</div> <!-- Se usa para volver a seleccionar la categoría de tu interés una vez finalices tu busqueda -->

            <!-- Condicional que indica todo lo que continua solo se aplica para los usuarios 1 que son los de Ciudadanía -->
            <div v-if="ID == 1" class="d-flex flex-wrap justify-content-center">

                <!-- Buscador en el archivo json sobre convivencia ciudadana -->
                <div v-for="(cursoconvivenciaCiudadana, identificador) in cursos.convivenciaCiudadana" :key="cursoconvivenciaCiudadana.id">
                    <div v-if="cursoconvivenciaCiudadana.nombre.trim().toLowerCase().indexOf(buscar.toLowerCase()) !== -1">
                        <div v-if="cursoconvivenciaCiudadana.requisitos.estado == 'activo' && cursoconvivenciaCiudadana.requisitos.ofertado && cursoconvivenciaCiudadana.requisitos.usuario == 1" class="accordion-item index-cursos-accordion">
                            <h2 class="accordion-header" id="acordion1">
                                <button class="index-cursos-accordion-button" type="button" data-bs-toggle="collapse" :data-bs-target="'#'+identificador" aria-expanded="false" :aria-controls="identificador">
                                    <img :src="cursoconvivenciaCiudadana.figure.imagen" :alt="cursoconvivenciaCiudadana.figure.alt" class="rounded" width="300px">
                                    <p class="index-cursos-titulo-accordion">
                                        <strong>{{ cursoconvivenciaCiudadana.nombre }}</strong> <br>
                                        <i>Categoría: {{ cursoconvivenciaCiudadana.categoria }}</i> <br>
                                    </p>
                                    <span>Conoce Más...</span>
                                </button>
                            </h2>
                            <div :id="identificador" class="collapse" aria-labelledby="acordion1" data-bs-parent="#home-accordion">
                                <div class="index-cursos-cuerpo-accordion">
                                    <div class="d-flex align-items-center">
                                        {{ cursoconvivenciaCiudadana.contenido }}
                                    </div>
                                    <div v-if="cursoconvivenciaCiudadana.requisitos.botonInscribir == 'si'" class="d-flex justify-content-center">
                                        <a :href="cursoconvivenciaCiudadana.requisitos.link" class="index-cursos-button-inscribete" target="_blank">INSCRIBETE</a>
                                    </div>
                                </div>
                            </div>
                        </div>
                    </div>
                </div>

                <!-- Buscador en el archivo json sobre Diversidad de género -->
                <div class="d-none" v-for="(cursodiversidadGenero, identificador) in cursos.diversidadGenero" :key="cursodiversidadGenero.id">
                    <div v-if="cursodiversidadGenero.nombre.trim().toLowerCase().indexOf(buscar.toLowerCase()) !== -1">
                        <div v-if="cursodiversidadGenero.requisitos.estado == 'activo' && cursodiversidadGenero.requisitos.ofertado && cursodiversidadGenero.requisitos.usuario == 1" class="accordion-item index-cursos-accordion">
                            <h2 class="accordion-header" id="acordion1">
                                <button class="index-cursos-accordion-button" type="button" data-bs-toggle="collapse" :data-bs-target="'#'+identificador" aria-expanded="false" :aria-controls="identificador">
                                    <img :src="cursodiversidadGenero.figure.imagen" :alt="cursodiversidadGenero.figure.alt" class="rounded" width="300px">
                                    <p class="index-cursos-titulo-accordion">
                                        <strong>{{ cursodiversidadGenero.nombre }}</strong> <br>
                                        <i>Categoría: {{ cursodiversidadGenero.categoria }}</i> <br>
                                    </p>
                                    <span>Conoce Más...</span>
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

                <!-- Buscador en el archivo json sobre gesstión humana -->
                <div class="d-none" v-for="(cursogestionHumana, identificador) in cursos.gestionHumana" :key="cursogestionHumana.id">
                    <div v-if="cursogestionHumana.nombre.trim().toLowerCase().indexOf(buscar.toLowerCase()) !== -1">
                        <div v-if="cursogestionHumana.requisitos.estado == 'activo' && cursogestionHumana.requisitos.ofertado && cursogestionHumana.requisitos.usuario == 1" class="accordion-item index-cursos-accordion">
                            <h2 class="accordion-header" id="acordion1">
                                <button class="index-cursos-accordion-button" type="button" data-bs-toggle="collapse" :data-bs-target="'#'+identificador" aria-expanded="false" :aria-controls="identificador">
                                    <img :src="cursogestionHumana.figure.imagen" :alt="cursogestionHumana.figure.alt" class="rounded" width="300px">
                                    <p class="index-cursos-titulo-accordion">
                                        <strong>{{ cursogestionHumana.nombre }}</strong> <br>
                                        <i>Categoría: {{ cursogestionHumana.categoria }}</i> <br>
                                    </p>
                                    <span>Conoce Más...</span>
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

                <!--Buscador en el archivo json sobre hacienda y contratación -->
                <div class="d-none" v-for="(cursohaciendaContratacion, identificador) in cursos.haciendaContratacion" :key="cursohaciendaContratacion.id">
                    <div v-if="cursohaciendaContratacion.nombre.trim().toLowerCase().indexOf(buscar.toLowerCase()) !== -1">
                        <div v-if="cursohaciendaContratacion.requisitos.estado == 'activo' && cursohaciendaContratacion.requisitos.ofertado && cursohaciendaContratacion.requisitos.usuario == 1" class="accordion-item index-cursos-accordion">
                            <h2 class="accordion-header" id="acordion1">
                                <button class="index-cursos-accordion-button" type="button" data-bs-toggle="collapse" :data-bs-target="'#'+identificador" aria-expanded="false" :aria-controls="identificador">
                                    <img :src="cursohaciendaContratacion.figure.imagen" :alt="cursohaciendaContratacion.figure.alt" class="rounded" width="300px">
                                    <p class="index-cursos-titulo-accordion">
                                        <strong>{{ cursohaciendaContratacion.nombre }}</strong> <br>
                                        <i>Categoría: {{ cursohaciendaContratacion.categoria }}</i> <br>
                                    </p>
                                    <span>Conoce Más...</span>
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

                <!-- Buscador en el archivo json sobre inclusión social -->
                <div class="d-none" v-for="(cursoinclusionSocial, identificador) in cursos.inclusionSocial" :key="cursoinclusionSocial.id">
                    <div v-if="cursoinclusionSocial.nombre.trim().toLowerCase().indexOf(buscar.toLowerCase()) !== -1">
                        <div v-if="cursoinclusionSocial.requisitos.estado == 'activo' && cursoinclusionSocial.requisitos.ofertado && cursoinclusionSocial.requisitos.usuario == 1" class="accordion-item index-cursos-accordion">
                            <h2 class="accordion-header" id="acordion1">
                                <button class="index-cursos-accordion-button" type="button" data-bs-toggle="collapse" :data-bs-target="'#'+identificador" aria-expanded="false" :aria-controls="identificador">
                                    <img :src="cursoinclusionSocial.figure.imagen" :alt="cursoinclusionSocial.figure.alt" class="rounded" width="300px">
                                    <p class="index-cursos-titulo-accordion">
                                        <strong>{{ cursoinclusionSocial.nombre }}</strong> <br>
                                        <i>Categoría: {{ cursoinclusionSocial.categoria }}</i> <br>
                                    </p>
                                    <span>Conoce Más...</span>
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

                <!-- Buscador en el archivo json sobre Salud -->
                <div class="d-none" v-for="(cursosalud, identificador) in cursos.salud" :key="cursosalud.id">
                    <div v-if="cursosalud.nombre.trim().toLowerCase().indexOf(buscar.toLowerCase()) !== -1">
                        <div v-if="cursosalud.requisitos.estado == 'activo' && cursosalud.requisitos.ofertado && cursosalud.requisitos.usuario == 1" class="accordion-item index-cursos-accordion">
                            <h2 class="accordion-header" id="acordion1">
                                <button class="index-cursos-accordion-button" type="button" data-bs-toggle="collapse" :data-bs-target="'#'+identificador" aria-expanded="false" :aria-controls="identificador">
                                    <img :src="cursosalud.figure.imagen" :alt="cursosalud.figure.alt" class="rounded" width="300px">
                                    <p class="index-cursos-titulo-accordion">
                                        <strong>{{ cursosalud.nombre }}</strong> <br>
                                        <i>Categoría: {{ cursosalud.categoria }}</i> <br>
                                    </p>
                                    <span>Conoce Más...</span>
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

                <!-- Buscador en el archivo json sobre seguridad vial -->
                <div v-for="(cursoseguridadVial, identificador) in cursos.seguridadVial" :key="cursoseguridadVial.id">
                    <div v-if="cursoseguridadVial.nombre.trim().toLowerCase().indexOf(buscar.toLowerCase()) !== -1">
                        <div v-if="cursoseguridadVial.requisitos.estado == 'activo' && cursoseguridadVial.requisitos.ofertado && cursoseguridadVial.requisitos.usuario == 1" class="accordion-item index-cursos-accordion">
                            <h2 class="accordion-header" id="acordion1">
                                <button class="index-cursos-accordion-button" type="button" data-bs-toggle="collapse" :data-bs-target="'#'+identificador" aria-expanded="false" :aria-controls="identificador">
                                    <img :src="cursoseguridadVial.figure.imagen" :alt="cursoseguridadVial.figure.alt" class="rounded" width="300px">
                                    <p class="index-cursos-titulo-accordion">
                                        <strong>{{ cursoseguridadVial.nombre }}</strong> <br>
                                        <i>Categoría: {{ cursoseguridadVial.categoria }}</i> <br>
                                    </p>
                                    <span>Conoce Más...</span>
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

                <!-- Buscador en el archivo json sobre seguridad y salud en el trabajo -->
                <div class="d-none" v-for="(cursoseguridadSaludTrabajo, identificador) in cursos.seguridadcursoseguridadSaludTrabajo" :key="cursoseguridadSaludTrabajo.id">
                    <div v-if="cursoseguridadSaludTrabajo.nombre.trim().toLowerCase().indexOf(buscar.toLowerCase()) !== -1">
                        <div v-if="cursoseguridadSaludTrabajo.requisitos.estado == 'activo' && cursoseguridadSaludTrabajo.requisitos.ofertado && cursoseguridadSaludTrabajo.requisitos.usuario == 1" class="accordion-item index-cursos-accordion">
                            <h2 class="accordion-header" id="acordion1">
                                <button class="index-cursos-accordion-button" type="button" data-bs-toggle="collapse" :data-bs-target="'#'+identificador" aria-expanded="false" :aria-controls="identificador">
                                    <img :src="cursoseguridadSaludTrabajo.figure.imagen" :alt="cursoseguridadSaludTrabajo.figure.alt" class="rounded" width="300px">
                                    <p class="index-cursos-titulo-accordion">
                                        <strong>{{ cursoseguridadSaludTrabajo.nombre }}</strong> <br>
                                        <i>Categoría: {{ cursoseguridadSaludTrabajo.categoria }}</i> <br>
                                    </p>
                                    <span>Conoce Más...</span>
                                </button>
                            </h2>
                            <div :id="identificador" class="collapse" aria-labelledby="acordion1" data-bs-parent="#home-accordion">
                                <div class="index-cursos-cuerpo-accordion">
                                    <div class="d-flex align-items-center">
                                        {{ cursoseguridadSaludTrabajo.contenido }}
                                    </div>
                                    <div v-if="cursoseguridadSaludTrabajo.requisitos.botonInscribir == 'si'" class="d-flex justify-content-center">
                                        <a :href="cursoseguridadSaludTrabajo.requisitos.link" class="index-cursos-button-inscribete" target="_blank">INSCRIBETE</a>
                                    </div>
                                </div>
                            </div>
                        </div>
                    </div>
                </div>

                <!-- Buscador en el archivo json sobre seminarios -->
                <div class="d-none" v-for="(cursoseminarios, identificador) in cursos.seminarios" :key="cursoseminarios.id">
                    <div v-if="cursoseminarios.nombre.trim().toLowerCase().indexOf(buscar.toLowerCase()) !== -1">
                        <div v-if="cursoseminarios.requisitos.estado == 'activo' && cursoseminarios.requisitos.ofertado && cursoseminarios.requisitos.usuario == 1" class="accordion-item index-cursos-accordion">
                            <h2 class="accordion-header" id="acordion1">
                                <button class="index-cursos-accordion-button" type="button" data-bs-toggle="collapse" :data-bs-target="'#'+identificador" aria-expanded="false" :aria-controls="identificador">
                                    <img :src="cursoseminarios.figure.imagen" :alt="cursoseminarios.figure.alt" class="rounded" width="300px">
                                    <p class="index-cursos-titulo-accordion">
                                        <strong>{{ cursoseminarios.nombre }}</strong> <br>
                                        <i>Categoría: {{ cursoseminarios.categoria }}</i> <br>
                                    </p>
                                    <span>Conoce Más...</span>
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

                <!-- Buscador en el archivo json sobre social -->
                <div v-for="(cursosocial, identificador) in cursos.social" :key="cursosocial.id">
                    <div v-if="cursosocial.nombre.trim().toLowerCase().indexOf(buscar.toLowerCase()) !== -1">
                        <div v-if="cursosocial.requisitos.estado == 'activo' && cursosocial.requisitos.ofertado && cursosocial.requisitos.usuario == 1" class="accordion-item index-cursos-accordion">
                            <h2 class="accordion-header" id="acordion1">
                                <button class="index-cursos-accordion-button" type="button" data-bs-toggle="collapse" :data-bs-target="'#'+identificador" aria-expanded="false" :aria-controls="identificador">
                                    <img :src="cursosocial.figure.imagen" :alt="cursosocial.figure.alt" class="rounded" width="300px">
                                    <p class="index-cursos-titulo-accordion">
                                        <strong>{{ cursosocial.nombre }}</strong> <br>
                                        <i>Categoría: {{ cursosocial.categoria }}</i> <br>
                                    </p>
                                    <span>Conoce Más...</span>
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

                <!-- Buscador en el archivo json sobre tecnología e innovación -->
                <div v-for="(cursotecnologiaInnovacion, identificador) in cursos.tecnologiaInnovacion" :key="cursotecnologiaInnovacion.id">
                    <div v-if="cursotecnologiaInnovacion.nombre.trim().toLowerCase().indexOf(buscar.toLowerCase()) !== -1">
                        <div v-if="cursotecnologiaInnovacion.requisitos.estado == 'activo' && cursotecnologiaInnovacion.requisitos.ofertado && cursotecnologiaInnovacion.requisitos.usuario == 1" class="accordion-item index-cursos-accordion">
                            <h2 class="accordion-header" id="acordion1">
                                <button class="index-cursos-accordion-button" type="button" data-bs-toggle="collapse" :data-bs-target="'#'+identificador" aria-expanded="false" :aria-controls="identificador">
                                    <img :src="cursotecnologiaInnovacion.figure.imagen" :alt="cursotecnologiaInnovacion.figure.alt" class="rounded" width="300px">
                                    <p class="index-cursos-titulo-accordion">
                                        <strong>{{ cursotecnologiaInnovacion.nombre }}</strong> <br>
                                        <i>Categoría: {{ cursotecnologiaInnovacion.categoria }}</i> <br>
                                    </p>
                                    <span>Conoce Más...</span>
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

            <!-- Condicional que indica todo lo que continua solo se aplica para los usuarios 2 que son los Servidores -->
            <div v-if="ID == 2" class="d-flex flex-wrap justify-content-center">

                <!-- Buscador en el archivo json sobre convivencia ciudadana -->
                <div v-for="(cursoconvivenciaCiudadana, identificador) in cursos.convivenciaCiudadana" :key="cursoconvivenciaCiudadana.id">
                    <div v-if="cursoconvivenciaCiudadana.nombre.trim().toLowerCase().indexOf(buscar.toLowerCase()) !== -1">
                        <div v-if="cursoconvivenciaCiudadana.requisitos.estado == 'activo' && cursoconvivenciaCiudadana.requisitos.ofertado && (cursoconvivenciaCiudadana.requisitos.usuario == 1 || cursoconvivenciaCiudadana.requisitos.usuario == 2)" class="accordion-item index-cursos-accordion">
                            <h2 class="accordion-header" id="acordion1">
                                <button class="index-cursos-accordion-button" type="button" data-bs-toggle="collapse" :data-bs-target="'#'+identificador" aria-expanded="false" :aria-controls="identificador">
                                    <img :src="cursoconvivenciaCiudadana.figure.imagen" :alt="cursoconvivenciaCiudadana.figure.alt" class="rounded" width="300px">
                                    <p class="index-cursos-titulo-accordion">
                                        <strong>{{ cursoconvivenciaCiudadana.nombre }}</strong> <br>
                                        <i>Categoría: {{ cursoconvivenciaCiudadana.categoria }}</i> <br>
                                    </p>
                                    <span>Conoce Más...</span>
                                </button>
                            </h2>
                            <div :id="identificador" class="collapse" aria-labelledby="acordion1" data-bs-parent="#home-accordion">
                                <div class="index-cursos-cuerpo-accordion">
                                    <div class="d-flex align-items-center">
                                        {{ cursoconvivenciaCiudadana.contenido }}
                                    </div>
                                    <div v-if="cursoconvivenciaCiudadana.requisitos.botonInscribir == 'si'" class="d-flex justify-content-center">
                                        <a :href="cursoconvivenciaCiudadana.requisitos.link" class="index-cursos-button-inscribete" target="_blank">INSCRIBETE</a>
                                    </div>
                                </div>
                            </div>
                        </div>
                    </div>
                </div>

                <!-- Buscador en el archivo json sobre diversidad y género -->
                <div class="d-none" v-for="(cursodiversidadGenero, identificador) in cursos.diversidadGenero" :key="cursodiversidadGenero.id">
                    <div v-if="cursodiversidadGenero.nombre.trim().toLowerCase().indexOf(buscar.toLowerCase()) !== -1">
                        <div v-if="cursodiversidadGenero.requisitos.estado == 'activo' && cursodiversidadGenero.requisitos.ofertado && (cursodiversidadGenero.requisitos.usuario == 1 || cursodiversidadGenero.requisitos.usuario == 2)" class="accordion-item index-cursos-accordion">
                            <h2 class="accordion-header" id="acordion1">
                                <button class="index-cursos-accordion-button" type="button" data-bs-toggle="collapse" :data-bs-target="'#'+identificador" aria-expanded="false" :aria-controls="identificador">
                                    <img :src="cursodiversidadGenero.figure.imagen" :alt="cursodiversidadGenero.figure.alt" class="rounded" width="300px">
                                    <p class="index-cursos-titulo-accordion">
                                        <strong>{{ cursodiversidadGenero.nombre }}</strong> <br>
                                        <i>Categoría: {{ cursodiversidadGenero.categoria }}</i> <br>
                                    </p>
                                    <span>Conoce Más...</span>
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

                <!-- Buscador en el archivo json sobre gestión humana -->
                <div class="d-none" v-for="(cursogestionHumana, identificador) in cursos.gestionHumana" :key="cursogestionHumana.id">
                    <div v-if="cursogestionHumana.nombre.trim().toLowerCase().indexOf(buscar.toLowerCase()) !== -1">
                        <div v-if="cursogestionHumana.requisitos.estado == 'activo' && cursogestionHumana.requisitos.ofertado && (cursogestionHumana.requisitos.usuario == 1 || cursogestionHumana.requisitos.usuario == 2)" class="accordion-item index-cursos-accordion">
                            <h2 class="accordion-header" id="acordion1">
                                <button class="index-cursos-accordion-button" type="button" data-bs-toggle="collapse" :data-bs-target="'#'+identificador" aria-expanded="false" :aria-controls="identificador">
                                    <img :src="cursogestionHumana.figure.imagen" :alt="cursogestionHumana.figure.alt" class="rounded" width="300px">
                                    <p class="index-cursos-titulo-accordion">
                                        <strong>{{ cursogestionHumana.nombre }}</strong> <br>
                                        <i>Categoría: {{ cursogestionHumana.categoria }}</i> <br>
                                    </p>
                                    <span>Conoce Más...</span>
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

                <!-- Buscador en el archivo json sobre hacienda y contratación -->
                <div v-for="(cursohaciendaContratacion, identificador) in cursos.haciendaContratacion" :key="cursohaciendaContratacion.id">
                    <div v-if="cursohaciendaContratacion.nombre.trim().toLowerCase().indexOf(buscar.toLowerCase()) !== -1">
                        <div v-if="cursohaciendaContratacion.requisitos.estado == 'activo' && cursohaciendaContratacion.requisitos.ofertado && (cursohaciendaContratacion.requisitos.usuario == 1 || cursohaciendaContratacion.requisitos.usuario == 2)" class="accordion-item index-cursos-accordion">
                            <h2 class="accordion-header" id="acordion1">
                                <button class="index-cursos-accordion-button" type="button" data-bs-toggle="collapse" :data-bs-target="'#'+identificador" aria-expanded="false" :aria-controls="identificador">
                                    <img :src="cursohaciendaContratacion.figure.imagen" :alt="cursohaciendaContratacion.figure.alt" class="rounded" width="300px">
                                    <p class="index-cursos-titulo-accordion">
                                        <strong>{{ cursohaciendaContratacion.nombre }}</strong> <br>
                                        <i>Categoría: {{ cursohaciendaContratacion.categoria }}</i> <br>
                                    </p>
                                    <span>Conoce Más...</span>
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

                <!-- Buscador en el archivo json sobre inclusión social -->
                <div class="d-none" v-for="(cursoinclusionSocial, identificador) in cursos.inclusionSocial" :key="cursoinclusionSocial.id">
                    <div v-if="cursoinclusionSocial.nombre.trim().toLowerCase().indexOf(buscar.toLowerCase()) !== -1">
                        <div v-if="cursoinclusionSocial.requisitos.estado == 'activo' && cursoinclusionSocial.requisitos.ofertado && (cursoinclusionSocial.requisitos.usuario == 1 || cursoinclusionSocial.requisitos.usuario == 2)" class="accordion-item index-cursos-accordion">
                            <h2 class="accordion-header" id="acordion1">
                                <button class="index-cursos-accordion-button" type="button" data-bs-toggle="collapse" :data-bs-target="'#'+identificador" aria-expanded="false" :aria-controls="identificador">
                                    <img :src="cursoinclusionSocial.figure.imagen" :alt="cursoinclusionSocial.figure.alt" class="rounded" width="300px">
                                    <p class="index-cursos-titulo-accordion">
                                        <strong>{{ cursoinclusionSocial.nombre }}</strong> <br>
                                        <i>Categoría: {{ cursoinclusionSocial.categoria }}</i> <br>
                                    </p>
                                    <span>Conoce Más...</span>
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

                <!-- Buscador en el archivo json sobre salud -->
                <div class="d-none" v-for="(cursosalud, identificador) in cursos.salud" :key="cursosalud.id">
                    <div v-if="cursosalud.nombre.trim().toLowerCase().indexOf(buscar.toLowerCase()) !== -1">
                        <div v-if="cursosalud.requisitos.estado == 'activo' && cursosalud.requisitos.ofertado && (cursosalud.requisitos.usuario == 1 || cursosalud.requisitos.usuario == 2)" class="accordion-item index-cursos-accordion">
                            <h2 class="accordion-header" id="acordion1">
                                <button class="index-cursos-accordion-button" type="button" data-bs-toggle="collapse" :data-bs-target="'#'+identificador" aria-expanded="false" :aria-controls="identificador">
                                    <img :src="cursosalud.figure.imagen" :alt="cursosalud.figure.alt" class="rounded" width="300px">
                                    <p class="index-cursos-titulo-accordion">
                                        <strong>{{ cursosalud.nombre }}</strong> <br>
                                        <i>Categoría: {{ cursosalud.categoria }}</i> <br>
                                    </p>
                                    <span>Conoce Más...</span>
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

                <!-- Buscador en el archivo json sobre seguridad vial -->
                <div v-for="(cursoseguridadVial, identificador) in cursos.seguridadVial" :key="cursoseguridadVial.id">
                    <div v-if="cursoseguridadVial.nombre.trim().toLowerCase().indexOf(buscar.toLowerCase()) !== -1">
                        <div v-if="cursoseguridadVial.requisitos.estado == 'activo' && cursoseguridadVial.requisitos.ofertado && (cursoseguridadVial.requisitos.usuario == 1 || cursoseguridadVial.requisitos.usuario == 2)" class="accordion-item index-cursos-accordion">
                            <h2 class="accordion-header" id="acordion1">
                                <button class="index-cursos-accordion-button" type="button" data-bs-toggle="collapse" :data-bs-target="'#'+identificador" aria-expanded="false" :aria-controls="identificador">
                                    <img :src="cursoseguridadVial.figure.imagen" :alt="cursoseguridadVial.figure.alt" class="rounded" width="300px">
                                    <p class="index-cursos-titulo-accordion">
                                        <strong>{{ cursoseguridadVial.nombre }}</strong> <br>
                                        <i>Categoría: {{ cursoseguridadVial.categoria }}</i> <br>
                                    </p>
                                    <span>Conoce Más...</span>
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

                <!-- Buscador en el archivo json sobre seguridad y salud en el trabajo -->
                <div class="d-none" v-for="(cursoseguridadSaludTrabajo, identificador) in cursos.seguridadcursoseguridadSaludTrabajo" :key="cursoseguridadSaludTrabajo.id">
                    <div v-if="cursoseguridadSaludTrabajo.nombre.trim().toLowerCase().indexOf(buscar.toLowerCase()) !== -1">
                        <div v-if="cursoseguridadSaludTrabajo.requisitos.estado == 'activo' && cursoseguridadSaludTrabajo.requisitos.ofertado && (cursoseguridadSaludTrabajo.requisitos.usuario == 1 || cursoseguridadSaludTrabajo.requisitos.usuario == 2)" class="accordion-item index-cursos-accordion">
                            <h2 class="accordion-header" id="acordion1">
                                <button class="index-cursos-accordion-button" type="button" data-bs-toggle="collapse" :data-bs-target="'#'+identificador" aria-expanded="false" :aria-controls="identificador">
                                    <img :src="cursoseguridadSaludTrabajo.figure.imagen" :alt="cursoseguridadSaludTrabajo.figure.alt" class="rounded" width="300px">
                                    <p class="index-cursos-titulo-accordion">
                                        <strong>{{ cursoseguridadSaludTrabajo.nombre }}</strong> <br>
                                        <i>Categoría: {{ cursoseguridadSaludTrabajo.categoria }}</i> <br>
                                    </p>
                                    <span>Conoce Más...</span>
                                </button>
                            </h2>
                            <div :id="identificador" class="collapse" aria-labelledby="acordion1" data-bs-parent="#home-accordion">
                                <div class="index-cursos-cuerpo-accordion">
                                    <div class="d-flex align-items-center">
                                        {{ cursoseguridadSaludTrabajo.contenido }}
                                    </div>
                                    <div v-if="cursoseguridadSaludTrabajo.requisitos.botonInscribir == 'si'" class="d-flex justify-content-center">
                                        <a :href="cursoseguridadSaludTrabajo.requisitos.link" class="index-cursos-button-inscribete" target="_blank">INSCRIBETE</a>
                                    </div>
                                </div>
                            </div>
                        </div>
                    </div>
                </div>

                <!-- Buscador en el archivo json sobre seminarios -->
                <div class="d-none" v-for="(cursoseminarios, identificador) in cursos.seminarios" :key="cursoseminarios.id">
                    <div v-if="cursoseminarios.nombre.trim().toLowerCase().indexOf(buscar.toLowerCase()) !== -1">
                        <div v-if="cursoseminarios.requisitos.estado == 'activo' && cursoseminarios.requisitos.ofertado && (cursoseminarios.requisitos.usuario == 1 || cursoseminarios.requisitos.usuario == 2)" class="accordion-item index-cursos-accordion">
                            <h2 class="accordion-header" id="acordion1">
                                <button class="index-cursos-accordion-button" type="button" data-bs-toggle="collapse" :data-bs-target="'#'+identificador" aria-expanded="false" :aria-controls="identificador">
                                    <img :src="cursoseminarios.figure.imagen" :alt="cursoseminarios.figure.alt" class="rounded" width="300px">
                                    <p class="index-cursos-titulo-accordion">
                                        <strong>{{ cursoseminarios.nombre }}</strong> <br>
                                        <i>Categoría: {{ cursoseminarios.categoria }}</i> <br>
                                    </p>
                                    <span>Conoce Más...</span>
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

                <!-- Buscador en el archivo json sobre social -->
                <div v-for="(cursosocial, identificador) in cursos.social" :key="cursosocial.id">
                    <div v-if="cursosocial.nombre.trim().toLowerCase().indexOf(buscar.toLowerCase()) !== -1">
                        <div v-if="cursosocial.requisitos.estado == 'activo' && cursosocial.requisitos.ofertado && (cursosocial.requisitos.usuario == 1 || cursosocial.requisitos.usuario == 2)" class="accordion-item index-cursos-accordion">
                            <h2 class="accordion-header" id="acordion1">
                                <button class="index-cursos-accordion-button" type="button" data-bs-toggle="collapse" :data-bs-target="'#'+identificador" aria-expanded="false" :aria-controls="identificador">
                                    <img :src="cursosocial.figure.imagen" :alt="cursosocial.figure.alt" class="rounded" width="300px">
                                    <p class="index-cursos-titulo-accordion">
                                        <strong>{{ cursosocial.nombre }}</strong> <br>
                                        <i>Categoría: {{ cursosocial.categoria }}</i> <br>
                                    </p>
                                    <span>Conoce Más...</span>
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

                <!-- Buscador en el archivo json sobre tecnología e innovación -->
                <div v-for="(cursotecnologiaInnovacion, identificador) in cursos.tecnologiaInnovacion" :key="cursotecnologiaInnovacion.id">
                    <div v-if="cursotecnologiaInnovacion.nombre.trim().toLowerCase().indexOf(buscar.toLowerCase()) !== -1">
                        <div v-if="cursotecnologiaInnovacion.requisitos.estado == 'activo' && cursotecnologiaInnovacion.requisitos.ofertado && (cursotecnologiaInnovacion.requisitos.usuario == 1 || cursotecnologiaInnovacion.requisitos.usuario == 2)" class="accordion-item index-cursos-accordion">
                            <h2 class="accordion-header" id="acordion1">
                                <button class="index-cursos-accordion-button" type="button" data-bs-toggle="collapse" :data-bs-target="'#'+identificador" aria-expanded="false" :aria-controls="identificador">
                                    <img :src="cursotecnologiaInnovacion.figure.imagen" :alt="cursotecnologiaInnovacion.figure.alt" class="rounded" width="300px">
                                    <p class="index-cursos-titulo-accordion">
                                        <strong>{{ cursotecnologiaInnovacion.nombre }}</strong> <br>
                                        <i>Categoría: {{ cursotecnologiaInnovacion.categoria }}</i> <br>
                                    </p>
                                    <span>Conoce Más...</span>
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
        <!-- FIN Función del buscador -->

        <!-- En caso de que no se este buscando nada, vamos a visualizar lo siguiente -->
        <div v-else>
            <div class="index-cursos-menu">

                <!-- Menú que esta al lado izquierdo con todas las categorías que se pueden seleccionar -->
                <div id="sub-menus" class="d-block h-100 index-cursos-menu-sub">
                    <ul class="index-cursos-menu-ul">
                        <!-- Todos manejan el evento cambioCategoria() con un parametro para identificar la categoría -->
                        <li class="index-cursos-menu-ul-li" v-on:click="cambioCategoria(1)">
                            <span class="material-symbols-outlined mx-2">
                                arrow_circle_right
                            </span>
                            Convivencia ciudadana
                        </li>
                        <li class="d-none index-cursos-menu-ul-li" v-on:click="cambioCategoria(2)">
                            <span class="material-symbols-outlined mx-2">
                                arrow_circle_right
                            </span>
                            Diversidad y género
                        </li>
                        <li class="d-none index-cursos-menu-ul-li" v-on:click="cambioCategoria(3)">
                            <span class="material-symbols-outlined mx-2">
                                arrow_circle_right
                            </span>
                            Gestión humana
                        </li>
                        <li v-if="mostrarHacienda" class="index-cursos-menu-ul-li" v-on:click="cambioCategoria(4)">
                            <span class="material-symbols-outlined mx-2">
                                arrow_circle_right
                            </span>
                            Hacienda y contratación
                        </li>
                        <li class="d-none index-cursos-menu-ul-li" v-on:click="cambioCategoria(5)">
                            <span class="material-symbols-outlined mx-2">
                                arrow_circle_right
                            </span>
                            Inclusión social
                        </li>
                        <li class="d-none index-cursos-menu-ul-li" v-on:click="cambioCategoria(6)">
                            <span class="material-symbols-outlined mx-2">
                                arrow_circle_right
                            </span>
                            Salud
                        </li>
                        <li class="index-cursos-menu-ul-li" v-on:click="cambioCategoria(7)">
                            <span class="material-symbols-outlined mx-2">
                                arrow_circle_right
                            </span>
                            Seguridad vial
                        </li>
                        <li class="d-none index-cursos-menu-ul-li" v-on:click="cambioCategoria(8)">
                            <span class="material-symbols-outlined mx-2">
                                arrow_circle_right
                            </span>
                            Seguridad y salud en el trabajo
                        </li>
                        <li class="d-none index-cursos-menu-ul-li" v-on:click="cambioCategoria(9)">
                            <span class="material-symbols-outlined mx-2">
                                arrow_circle_right
                            </span>
                            Seminarios
                        </li>
                        <li class="index-cursos-menu-ul-li" v-on:click="cambioCategoria(10)">
                            <span class="material-symbols-outlined mx-2">
                                arrow_circle_right
                            </span>
                            Social
                        </li>
                        <li class="index-cursos-menu-ul-li" v-on:click="cambioCategoria(11)">
                            <span class="material-symbols-outlined mx-2">
                                arrow_circle_right
                            </span>
                            Tecnología e innovación
                        </li>
                    </ul>
                </div>

                <!-- Cursos que se muestran en la categoría seleccioniada dependiendo del usuario -->
                <!-- Usuario ciudadano 1 -->
                <div v-if="ID == 1" id="index-visualizacion" class="index-cursos-visualizacion">
                    <!-- Visualización de selección de categoría en dispositivos celulares o de tamaños similares -->
                    <div class="div-tema">
                        <label for="">Categoría:</label>
                        <select class="mx-3" v-model="categoriaResponsive" name="" v-on:change="verificarCategoria" id="select">
                            <option value="Convivencia ciudadana">Convivencia ciudadana</option>
                            <option value="Seguridad vial">Seguridad vial</option>
                            <option value="Social">Social</option>
                            <option value="Tecnología e innovación">Tecnología e innovación</option>
                        </select>
                    </div>
                    <!-- Visualización de los cursos además se envía el numero del curso para que identifique cual mostrar -->
                    <CpCiudadano id="CpCiudadano" class="w-100 h-100 d-flex align-items-center justify-content-center index-cursos-fondo" :propt="numeroCategoria" />
                </div>

                <!-- Usuario servidor 2 -->
                <div v-if="ID == 2" id="index-visualizacion-2" class="index-cursos-visualizacion">
                    <!-- Visualización de selección de categoría en dispositivos celulares o de tamaños similares -->
                    <div class="div-tema">
                        <label for="">Categoría:</label>
                        <select class="mx-3" v-model="categoriaResponsive" name="" v-on:change="verificarCategoria" id="select">
                            <option value="Convivencia ciudadana">Convivencia ciudadana</option>
                            <option value="Hacienda y contratación">Hacienda y contratación</option>
                            <option value="Seguridad vial">Seguridad vial</option>
                            <option value="Social">Social</option>
                            <option value="Tecnología e innovación">Tecnología e innovación</option>
                        </select>
                    </div>
                    <!-- Visualización de los cursos además se envía el numero del curso para que identifique cual mostrar -->
                    <CpServidor id="CpServidor" class="w-100 h-100 d-flex align-items-center justify-content-center index-cursos-fondo" :propt="numeroCategoria" />
                </div>

            </div>
        </div>

    </div>
</template>

<script>
// Se importa el archivo json
import datos from '../assets/cursos.json'
// Se importan los componentes que se van a utilizar
import CpCiudadano from '../components/CpCiudadano.vue'
import CpServidor from '../components/CpServidor.vue'

export default {
  data () {
    return {
      // cursos es la variable que contiene el archivo json en forma de objeto
      cursos: datos,
      // Indica la posición de la categoría que está, ya que cada una equivale a un valor entre 1 y 11
      numeroCategoria: 0,
      // Esta enlazada con la caja de texto con id 'buscador'
      buscar: '',
      // Guarda el valor de la categoría que se seleccióna
      categoriaResponsive: '',
      // Define si se añade o no la categoría de Hacienda y contratación de pendiendo si es Ciudadano o Servidor
      mostrarHacienda: false
    }
  },
  name: 'CpCursos',
  props: {
    // Se reciben las props que se envían desde el componente padre y se indica el tipo
    ID: {
      type: Number
    },
    indicadorTecnologia: {
      type: Number
    }
  },
  components: {
    CpCiudadano,
    CpServidor
  },
  // Estas funciones se activan apenas se realiza un render completo e ingresas al usuario
  mounted () {
    // Visualiza la categoría de Tecnología e Innovación solo si le das click al banner de la portada
    if (this.indicadorTecnologia === 11) {
      this.cambioCategoria(11)
    }
    // Activa la opción de Hacienda y contratación en el perfil de servidor
    if (this.ID === 2) {
      this.mostrarHacienda = true
    }
  },
  methods: {
    // Función que brinda la aparición de la caja de texto cuando estas en dispositivos celulares o pequeños
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
    // Función que solo se ejecuta en la versión responsive
    verificarCategoria () {
      // Identifica la categoría y ejecuta la función para visualizar la categoría
      if (this.categoriaResponsive === 'Convivencia ciudadana') {
        this.cambioCategoria(1)
      }
      if (this.categoriaResponsive === 'Diversidad y género') {
        this.cambioCategoria(2)
      }
      if (this.categoriaResponsive === 'Gestión humana') {
        this.cambioCategoria(3)
      }
      if (this.categoriaResponsive === 'Hacienda y contratación') {
        this.cambioCategoria(4)
      }
      if (this.categoriaResponsive === 'Inclusión social') {
        this.cambioCategoria(5)
      }
      if (this.categoriaResponsive === 'Salud') {
        this.cambioCategoria(6)
      }
      if (this.categoriaResponsive === 'Seguridad vial') {
        this.cambioCategoria(7)
      }
      if (this.categoriaResponsive === 'Seguridad y salud en el trabajo"') {
        this.cambioCategoria(8)
      }
      if (this.categoriaResponsive === 'Seminarios') {
        this.cambioCategoria(9)
      }
      if (this.categoriaResponsive === 'Social') {
        this.cambioCategoria(10)
      }
      if (this.categoriaResponsive === 'Tecnología e innovación') {
        this.cambioCategoria(11)
      }
    },
    // Función que hace que las categorías cambien entre si visualizandose unas y otras que lo define el parametro valor
    cambioCategoria (valor) {
      this.$emit('cambio', valor)
      // Elimina el fondo dependiendo del usuario que ingreso
      if (this.ID === 1) {
        document.getElementById('CpCiudadano').style.background = 'none'
      }
      if (this.ID === 2) {
        document.getElementById('CpServidor').style.background = 'none'
      }
      // Selecciones de categoría en versión para celulares o dispositivos pequeños a medianos
      if (window.screen.width < 769) {
        if (this.ID === 1) {
          const a = document.getElementById('sub-menus')
          a.classList.remove('index-cursos-menu-sub')
          a.classList.remove('d-block')
          a.classList.add('d-none')
          const b = document.getElementById('index-visualizacion')
          b.classList.add('d-block')
        }
        if (this.ID === 2) {
          const a = document.getElementById('sub-menus')
          a.classList.remove('index-cursos-menu-sub')
          a.classList.remove('d-block')
          a.classList.add('d-none')
          const b = document.getElementById('index-visualizacion-2')
          b.classList.add('d-block')
        }
      }
      // Agrega una clase de activación para identificar la categoría en la que estas
      this.numeroCategoria = valor
      const li = document.querySelectorAll('.index-cursos-menu-ul-li')
      if (this.mostrarHacienda) {
        for (let i = 0; i < li.length; i++) {
          if (li[valor - 1] === li[i]) {
            li[i].classList.add('index-cursos-menu-ul-li-activado')
          }
          if (li[i] !== li[valor - 1]) {
            li[i].classList.remove('index-cursos-menu-ul-li-activado')
          }
        }
      }
      if (!this.mostrarHacienda) {
        for (let i = 0; i < li.length; i++) {
          if (i < 4) {
            if (li[valor - 1] === li[i]) {
              li[i].classList.add('index-cursos-menu-ul-li-activado')
            }
            if (li[i] !== li[valor - 1]) {
              li[i].classList.remove('index-cursos-menu-ul-li-activado')
            }
          }
          if (i >= 4) {
            if (li[valor - 2] === li[i]) {
              li[i].classList.add('index-cursos-menu-ul-li-activado')
            }
            if (li[i] !== li[valor - 2]) {
              li[i].classList.remove('index-cursos-menu-ul-li-activado')
            }
          }
        }
      }
    }
  }
}
</script>
