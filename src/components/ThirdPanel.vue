<template>
    <div id="work">
        <borderTopSVG />
        <div id="work__headline">
            <h2>Mi Experiencia Laboral:</h2>
        </div>

        <div id="work__experience">
            <div class="work__job">
                <h3 class="work__company bold">Alebat Education</h3>
                <p class="work__role">Desarrollador Fullstack - Marzo 2021 -- Diciembre 2022</p>

                <div>
                    <ul>
                        <li>Inicios en PHP realizando proyectos en Wordpress y Woocommerce.</li>
                        <li>Desarrollo de proyectos de páginas web usando PHP y Javascript desde 0 (Sin Plantillas)</li>
                        <li>Participación junto a una persona más en un proyecto de rediseño de la página principal de
                            la marca de la empresa usando VueJS</li>
                        <li>Proyectos SPA/Landings y pequeñas aplicaciones usando VueJS.</li>
                        <li>Uso de APIs REST para la recogida y presentación de datos en los proyectos.</li>
                        <li>Mantenimiento de BBDD MySQL</li>
                        <li>Diseño, creación, implementación y mantenimiento de BBDD en la plataforma Amazon
                            DynamoDB (Uso de GraphQL)</li>
                        <li> Responsable de proyectos, gestión de equipos, testing y QA de los mismos.</li>
                        <li>Responsable de la creación y mantenimiento de versiones de proyectos en el Github de
                            Amazon (Codecommit)</li>
                    </ul>
                </div>
            </div>

            <div class="work__job">
                <h3 class="work__company bold"> redk - CRM & CX Transformation</h3>
                <p class="work__role">Zendesk Developer Junior (Front-end) - Febrero 2023 -- Junio 2023</p>

                <div>
                    <ul>
                        <li>Inicios en formación del framework de React JS.</li>
                        <li>Desarrollos y mantenimiento de aplicaciones en Zendesk usando javascript.</li>
                        <li>Tareas en la plataforma de Zendesk Guide para el manejo, representación de datos y su
                            posterior reflejo en tablas o gráficas para cliente.</li>
                        <li>Desarrollo y mantenimiento de scripts js para la automatización de datos.</li>
                    </ul>
                </div>
            </div>
        </div>
        <borderBottomSVG />
    </div>
</template>

<script setup lang="ts">
import borderTopSVG from '../assets/svg/BorderTopSVG.vue';
import borderBottomSVG from '../assets/svg/BorderBottomSVG.vue';
</script>