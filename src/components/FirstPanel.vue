<template>
    <div id="first" class="flex-centered">
        <borderTopSVG />
        <div id="first__panel" class="flex-column centered">
            <p class="fade-up">Iker Ocaña</p>
            <p class="fade-up second-delay">Full-Stack Junior Developer</p>
            <div class="logo-container fade-up third-delay">
                <picture>
                    <a href="https://www.linkedin.com/in/iker-oca%C3%B1a-7b30b41ba/" target="_blank"><img class="logo" src="../img/linkedin-logo.png" alt="Link a linkedin"></a>
                </picture>

                <picture>
                    <a href="https://github.com/iker-ocana" target="_blank"><img class="logo" src="../img/github-logo.png" alt="Link a github"></a>
                </picture>
            </div>
        </div>
        <borderBottomSVG />
    </div>
</template>

<script setup lang="ts">
import borderTopSVG from '../assets/svg/BorderTopSVG.vue';
import borderBottomSVG from '../assets/svg/BorderBottomSVG.vue';
</script>