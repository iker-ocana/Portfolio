<template>
    <div id="second" class="flex-between-column full-height">
        <borderTopSVG />
        <section id="second__container">
            <div class="frame-image flex centered">
                <img src="../img/foto-frontal.jpg"/>
            </div>

            <div>
                <div class="about-me">
                    <h2 class="about-me__headline bold">Sobre mi</h2>

                    <div class="about-me__introduction">
                        <p class="about-me__text">
                            Soy un desarrollador full stack con mucha pasión por el frontend y más de 2 años de experiencia en este sector laboral. 
                            Mi trayectoria profesional abarca desde proyectos en WordPress y WooCommerce con PHP hasta el desarrollo de aplicaciones 
                            utilizando Vue JS y React JS. 
                        </p>

                        <p class="about-me__text">
                            He tenido la oportunidad de trabajar en entornos ágiles como SCRUM y también he podido tener experiencia liderando proyectos, 
                            gestionando equipos y asegurando la calidad en cada etapa del desarrollo. Mi experiencia incluye, además, el manejo de bases de datos 
                            como MySQL y DynamoDB, así como la integración con APIs REST para la recogida y presentación de datos en diferentes lenguajes de programación. 
                        </p>

                        <p class="about-me__text">
                            Por otra parte, poseo un dominio intermedio-alto de inglés (certificación B2), lo que me permite comunicarme eficazmente en un entorno global y 
                            que ya he tenido que usar para comunicarme en mis anteriores experiencias laborales. Además, me gusta el constante desafio de solucionar problemas 
                            que surjan en los desarrollos, siempre he tenido una mentalidad de aprendizaje continuo y una capacidad demostrada para adaptarme a nuevas tecnologías. 
                        </p>

                        <p class="about-me__text">
                            Mi objetivo es seguir creciendo como desarrollador frontend, especializandome y  aprovechando al 100% mis habilidades técnicas y mi 
                            capacidad para trabajar en equipo para contribuir al éxito de proyectos emocionantes y desafiantes.
                        </p>
                    </div>
                </div>
            </div>
        </section>
        

        <section>
            <div>
                <p class="text-centered italic-font">¡Espero poder tener la oportunidad de hablar en más detalle de mi experiencia!</p>
            </div>
        </section>
        <borderBottomSVG />
    </div>
</template>

<script setup lang="ts">
import borderTopSVG from '../assets/svg/BorderTopSVG.vue';
import borderBottomSVG from '../assets/svg/BorderBottomSVG.vue';

</script>