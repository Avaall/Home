<template>
    <div>

        <!-- Header -->
        <div class="home-header">
            <div class="home-header-bg align-items-center d-flex">
                <div class="d-flex w-100 justify-content-between align-items-center">
                    <div class="home-header-texto">
                        <p class="home-header-texto-1 m-0">Alcaldía de Medellín</p>
                        <p class="home-header-texto-2 m-0">Escuela Virtual de Aprendizaje</p>
                    </div>
                    <div class="cursor" v-on:click="AbrirMenu">
                        <img src="../assets/img/boton-ingreso.png" alt="Botón de ingreso" class="img-ingreso">
                    </div>
                </div>
            </div>
        </div>
        <!-- FIN Header -->

        <!-- Body carousel -->
        <div id="carousel" class="carousel slide home-carousel" data-bs-ride="true">
            <!-- Indicadores de cuantas páginas tiene el banner -->
            <div class="carousel-indicators">
                <button type="button" data-bs-target="#carousel" data-bs-slide-to="0" class="active" aria-current="true" aria-label="Slide 1"></button>
                <button type="button" data-bs-target="#carousel" data-bs-slide-to="1" aria-label="Slide 2"></button>
                <button type="button" data-bs-target="#carousel" data-bs-slide-to="2" aria-label="Slide 3"></button>
            </div>
            <!-- Acá se reposita cada uno de los items o páginas del carousel, debe de coincidir con la cantidad de indicadores de pestañas para evitar bugs -->
            <div class="carousel-inner">
                <!-- Primer banner -->
                <div class="carousel-item carousel-item-unic active">
                    <div class="carousel-caption h-100" v-on:click="cambiarValor"></div>
                </div>
                <!-- Segundo banner -->
                <div class="carousel-item carousel-item-unic-2">
                    <div class="carousel-caption d-flex justify-content-center justify-content-sm-end h-100 align-items-center home-carousel-animation">
                        <img src="../assets/img/carousel-logo-escuela.png" alt="Imagen logo Escuela Virtual de Aprendizaje" class="img-info-caption info-caption">
                    </div>
                </div>
                <!-- Tercer banner -->
                <div class="carousel-item carousel-item-unic-3">
                    <div class="carousel-caption d-flex flex-column justify-content-center h-100 align-items-center">
                        <div class="home-carousel-text home-carousel-animation">
                            <center class="info-caption-text"><span>La <strong>Escuela Virtual de Aprendizaje</strong><br>es un espacio para compartir,<br> explorar y descubrir conocimientos</span></center>
                        </div>
                    </div>
                </div>
            </div>
            <!-- Botones para avanzar y volver entre items -->
            <button class="carousel-control-prev" type="button" data-bs-target="#carousel" data-bs-slide="prev">
                <span class="carousel-control-prev-icon" aria-hidden="true"></span>
                <span class="visually-hidden">Previous</span>
            </button>
            <button class="carousel-control-next" type="button" data-bs-target="#carousel" data-bs-slide="next">
                <span class="carousel-control-next-icon" aria-hidden="true"></span>
                <span class="visually-hidden">Next</span>
            </button>
        </div>
        <!-- FIN Body carousel -->

        <!-- Información adicional para el Conoce Más -->
        <section id="home-section" class="home-section">
            <div class="home-informacion">

            <!-- ¿Qué es la Escuela Virtual de Aprpendizaje? -->
                <!-- Imagen y titulo que se visualiza -->
                <div class="home-informacion-button" v-on:click="MostrarInfoButton(0)">
                    <img src="../assets/img/modal-icon-1.png" alt="Imagen referente a ¿Qué es la Escuela Virtual de Aprendizaje?" class="mt-2 home-icon-informacion">
                    <p class="text-center mx-2 home-valor-texto-titulo">¿Qué es la Escuela Virtual de Aprendizaje?</p>
                </div>
                <div class="home-informacion-body">
                    <!-- Información para computadores o dispositivos grades -->
                    <p>
                        Es una de las estrategias de formación, capacitación y entrenamiento de
                        la Alcaldía de Medellín para fortalecer las <strong>competencias</strong> y <strong>capacidades</strong> de
                        los servidores públicos y de la ciudadanía, mediante programas de
                        aprendizaje con énfasis en diferentes temáticas. <br><br>

                        La <strong>misión</strong> de la Escuela es facilitar los procesos de enseñanza y aprendizaje
                        desde el <strong>SER</strong> (formación), el <strong>HACER</strong> (entrenamiento) y el <strong>SABER</strong> (capacitación).
                    </p>
                    <div>
                        <button v-on:click="cerrar(0)">Cerrar</button>
                    </div>
                </div>
                <div class="home-informacion-body-responsive">
                    <!-- Información para celulares o dispositivos pequeños -->
                    <p>
                        Es una de las estrategias de formación, capacitación y entrenamiento de
                        la Alcaldía de Medellín para fortalecer las <strong>competencias</strong> y <strong>capacidades</strong> de
                        los servidores públicos y de la ciudadanía, mediante programas de
                        aprendizaje con énfasis en diferentes temáticas. <br><br>

                        La <strong>misión</strong> de la Escuela es facilitar los procesos de enseñanza y aprendizaje
                        desde el <strong>SER</strong> (formación), el <strong>HACER</strong> (entrenamiento) y el <strong>SABER</strong> (capacitación).
                    </p>
                </div>
                <div class="home-informacion-body-responsive-md">
                    <!-- Información para tablets o dispositivos con un tamaño mediano -->
                    <p>
                        Es una de las estrategias de formación, capacitación y entrenamiento de
                        la Alcaldía de Medellín para fortalecer las <strong>competencias</strong> y <strong>capacidades</strong> de
                        los servidores públicos y de la ciudadanía, mediante programas de
                        aprendizaje con énfasis en diferentes temáticas. <br><br>

                        La <strong>misión</strong> de la Escuela es facilitar los procesos de enseñanza y aprendizaje
                        desde el <strong>SER</strong> (formación), el <strong>HACER</strong> (entrenamiento) y el <strong>SABER</strong> (capacitación).
                    </p>
                    <div>
                        <button v-on:click="cerrar(0)">Cerrar</button>
                    </div>
                </div>

            <!-- ¿Qué necesito para acceder? -->
                <!-- Imagen y titulo que se visualiza -->
                <div class="home-informacion-button" v-on:click="MostrarInfoButton(1)">
                    <img src="../assets/img/modal-icon-2.png" alt="Imagen referente a ¿Qué necesito para acceder?" class="mt-2 home-icon-informacion">
                    <p class="text-center mx-2 home-valor-texto-titulo">¿Qué necesito <br> para acceder?</p>
                </div>
                <div class="home-informacion-body">
                    <!-- Información para computadores -->
                    <p><strong>Para acceder a los cursos ofertados debes cumplir con los siguientes requisitos:</strong></p>
                    <p><strong>-</strong> Ser residente del Distrito de Medellín. <br>
                    <strong>-</strong> Contar con un computador, tablet o teléfono móvil con conexión a internet estable. <br>
                    <strong>-</strong> Tener un correo electrónico activo, ya que a este será enviada la confirmación de
                        inscripción y toda la información relacionada con el curso al que te inscribas. <br>
                    <strong>-</strong> ¡Muchas ganas de aprender!</p>
                    <div>
                        <button v-on:click="cerrar(1)">Cerrar</button>
                    </div>
                </div>
                <div class="home-informacion-body-responsive">
                    <!-- Información para celulares o dispositivos pequeños -->
                    <p><strong>Para acceder a los cursos ofertados debes cumplir con los siguientes requisitos:</strong></p>
                    <p><strong>-</strong> Ser residente del Distrito de Medellín. <br>
                    <strong>-</strong> Contar con un computador, tablet o teléfono móvil con conexión a internet estable. <br>
                    <strong>-</strong> Tener un correo electrónico activo, ya que a este será enviada la confirmación de
                        inscripción y toda la información relacionada con el curso al que te inscribas. <br>
                    <strong>-</strong> ¡Muchas ganas de aprender!</p>
                </div>
                <div class="home-informacion-body-responsive-md">
                    <!-- Información para tablets o dispositivos con un tamaño mediano -->
                    <p><strong>Para acceder a los cursos ofertados debes cumplir con los siguientes requisitos:</strong></p>
                    <p><strong>-</strong> Ser residente del Distrito de Medellín. <br>
                    <strong>-</strong> Contar con un computador, tablet o teléfono móvil con conexión a internet estable. <br>
                    <strong>-</strong> Tener un correo electrónico activo, ya que a este será enviada la confirmación de
                        inscripción y toda la información relacionada con el curso al que te inscribas. <br>
                    <strong>-</strong> ¡Muchas ganas de aprender!</p>
                    <div>
                        <button v-on:click="cerrar(1)">Cerrar</button>
                    </div>
                </div>

            <!-- ¿Qué puedo aprender aquí? -->
                <!-- Imagen y titulo que se visualiza -->
                <div class="home-informacion-button" v-on:click="MostrarInfoButton(2)">
                    <img src="../assets/img/modal-icon-3.png" alt="Imagen referente a ¿Qué puedo aprender aquí?" class="mt-2 home-icon-informacion">
                    <p class="text-center mx-2 home-valor-texto-titulo">¿Qué puedo <br> aprender aquí?</p>
                </div>
                <div class="home-informacion-body">
                    <!-- Información para computadores -->
                    En la Escuela Virtual de Aprendizaje encontrarás cursos gratuitos que te permitirán
                    obtener nuevos conocimientos o fortalecer los que ya tienes en diferentes áreas como:
                    tecnología e innovación, diversidad y equidad de género, prevención del embarazo en la
                    adolescencia, entre otros. Al finalizar los cursos recibirás un certificado de participación.
                    <div>
                        <button v-on:click="cerrar(2)">Cerrar</button>
                    </div>
                </div>
                <div class="home-informacion-body-responsive">
                    <!-- Información para celulares o dispositivos pequeños -->
                    En la Escuela Virtual de Aprendizaje encontrarás cursos gratuitos que te permitirán
                    obtener nuevos conocimientos o fortalecer los que ya tienes en diferentes áreas como:
                    tecnología e innovación, diversidad y equidad de género, prevención del embarazo en la
                    adolescencia, entre otros. Al finalizar los cursos recibirás un certificado de participación.
                </div>
                <div class="home-informacion-body-responsive-md">
                    <!-- Información para tablets o dispositivos con un tamaño mediano -->
                    En la Escuela Virtual de Aprendizaje encontrarás cursos gratuitos que te permitirán
                    obtener nuevos conocimientos o fortalecer los que ya tienes en diferentes áreas como:
                    tecnología e innovación, diversidad y equidad de género, prevención del embarazo en la
                    adolescencia, entre otros. Al finalizar los cursos recibirás un certificado de participación.
                    <div>
                        <button v-on:click="cerrar(2)">Cerrar</button>
                    </div>
                </div>

            <!-- ¿Cómo inscribirme? -->
                <!-- Imagen y titulo que se visualiza -->
                <div class="home-informacion-button" v-on:click="MostrarInfoButton(3)">
                    <img src="../assets/img/modal-icon-4.png" alt="Imagen referente a ¿Cómo inscribirme?" class="mt-2 home-icon-informacion">
                    <p class="text-center mx-2 home-valor-texto-titulo">¿Cómo inscribirme? <br> &nbsp;</p>
                </div>
                <div class="home-informacion-body">
                    <!-- Información para computadores -->
                    <p><strong>1.</strong> Elige los cursos de tu interés. <br>
                    <strong>2.</strong> Haz clic en <strong>"Inscríbete"</strong>. <br>
                    <strong>3.</strong> Digita tus datos en el formulario de inscripción y luego haz clic en <strong>"Enviar"</strong>. <br>
                    <strong>4.</strong> Espera el mensaje de confirmación que llegará a tu correo durante las próximas 24
                    horas para el inicio del curso. Revisa que el mensaje no llegue a la carpeta de spam. <br>
                    <strong>5.</strong> Luego de recibir tu usuario y contraseña para iniciar el curso, podrás acceder al
                        <strong>campus virtual</strong> para empezar tu proceso formativo. <br>
                    <strong>6.</strong> Recuerda que los cursos son <strong>gratuitos</strong> y al finalizar recibes <strong>certificado de participación</strong>.</p>
                    <div>
                        <button v-on:click="cerrar(3)">Cerrar</button>
                    </div>
                </div>
                <div class="home-informacion-body-responsive">
                    <!-- Información para celulares o dispositivos pequeños -->
                    <p><strong>1.</strong> Elige los cursos de tu interés. <br>
                    <strong>2.</strong> Haz clic en <strong>"Inscríbete"</strong>. <br>
                    <strong>3.</strong> Digita tus datos en el formulario de inscripción y luego haz clic en <strong>"Enviar"</strong>. <br>
                    <strong>4.</strong> Espera el mensaje de confirmación que llegará a tu correo durante las próximas 24
                    horas para el inicio del curso. Revisa que el mensaje no llegue a la carpeta de spam. <br>
                    <strong>5.</strong> Luego de recibir tu usuario y contraseña para iniciar el curso, podrás acceder al</p>
                    <p><strong>campus virtual</strong> para empezar tu proceso formativo. <br>
                    <strong>6.</strong> Recuerda que los cursos son <strong>gratuitos</strong> y al finalizar recibes <strong>certificado de participación</strong>.</p>
                </div>
                <div class="home-informacion-body-responsive-md">
                    <!-- Información para tablets o dispositivos con un tamaño mediano -->
                    <p><strong>1.</strong> Elige los cursos de tu interés. <br>
                    <strong>2.</strong> Haz clic en <strong>"Inscríbete"</strong>. <br>
                    <strong>3.</strong> Digita tus datos en el formulario de inscripción y luego haz clic en <strong>"Enviar"</strong>. <br>
                    <strong>4.</strong> Espera el mensaje de confirmación que llegará a tu correo durante las próximas 24
                    horas para el inicio del curso. Revisa que el mensaje no llegue a la carpeta de spam. <br>
                    <strong>5.</strong> Luego de recibir tu usuario y contraseña para iniciar el curso, podrás acceder al</p>
                    <p><strong>campus virtual</strong> para empezar tu proceso formativo. <br>
                    <strong>6.</strong> Recuerda que los cursos son <strong>gratuitos</strong> y al finalizar recibes <strong>certificado de participación</strong>.</p>
                    <div>
                        <button v-on:click="cerrar(3)">Cerrar</button>
                    </div>
                </div>

            </div>
        </section>
        <!-- FIN Información adicional para el Conoce Más -->

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
export default {
  methods: {
    // Función para abrir el menú
    AbrirMenu () {
      document.getElementById('usuario-ingresar').style.top = '0px'
    },
    // Función que activa una función en el componente padre para redireccionar a la categoría tecnología
    cambiarValor () {
      this.$emit('cambiarValor')
    },
    // Función para visualizar la información de los botones en el home
    MostrarInfoButton (i) {
      const informacion = document.querySelectorAll('.home-informacion-body')
      const informacionResponsive = document.querySelectorAll('.home-informacion-body-responsive-md')
      const button = document.querySelectorAll('.home-informacion-button')
      for (let x = 0; x < informacion.length; x++) {
        if (screen.width < 1200 && screen.width > 560) {
          if (x === i) {
            informacionResponsive[i].style.margin = '20px 0'
            informacionResponsive[i].style.width = '300px'
            informacionResponsive[i].style.display = 'flex'
            informacionResponsive[i].style.padding = '20px'
            informacionResponsive[i].style.boxShadow = '0 0px 20px rgba(0, 0, 0, 0.20)'
          }
          if (x !== i) {
            button[x].style.display = 'none'
            informacionResponsive[x].style.display = 'none'
          }
        }
        if (screen.width > 1200) {
          if (x === i) {
            informacion[i].style.animation = 'home-informacion-aparecer forwards 1s'
          }
          if (x !== i) {
            button[x].style.display = 'none'
          }
        }
      }
    },
    // Función para cerrar la visualización de los botones en el home
    cerrar (i) {
      const button = document.querySelectorAll('.home-informacion-button')
      const informacionResponsive = document.querySelectorAll('.home-informacion-body-responsive-md')
      const informacion = document.querySelectorAll('.home-informacion-body')
      for (let x = 0; x < informacion.length; x++) {
        if (screen.width < 1200 && screen.width > 560) {
          if (x === i) {
            informacionResponsive[i].style.display = 'none'
          }
          if (x !== i) {
            button[x].style.display = 'flex'
            informacionResponsive[x].style.display = 'none'
          }
        }
        if (screen.width > 1200) {
          if (x === i) {
            informacion[i].style.animation = ''
          }
          if (x !== i) {
            button[x].style.display = 'flex'
          }
        }
      }
    }
  },
  name: 'IndexIncio'
}
</script>
