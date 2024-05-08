<template>
    <div id="knowledge">
        <borderTopSVG />
        <section class="knowledge__title">
            <h2 class="text-centered bold">Conocimientos adquiridos a lo largo de mi experiencia laboral</h2>
        </section>

        <section id="knowledge__container">
            <div v-for="item in knowledge" class="item" @click="knowledgeSwap(item.panel)">
                <img :src="getLogoImgUrl(item.logo)">
            </div>
        </section>

        <section class="knowledge__expand" ref="knowledgeContainer">
            <div class="circle" :class="{ 'circle_cover': circleCover }"></div>
            <div class="moving-circle" :class="{ 'moving-circle-opacity': miniCirclesOff }" v-for="circle in 6"
                ref="movingCircles"></div>
            <Transition appear name="transition-component" mode="out-in" @onBeforeLeave="onLeave" @onBeforeEnter="onEnter">
                <component :is='knowledgePanel' :class="{ 'onComponentEnter': onComponentEnter }"></component>
            </Transition>
        </section>
        <borderBottomSVG />
    </div>
</template>

<script setup lang="ts">

import borderTopSVG from '../assets/svg/BorderTopSVG.vue';
import borderBottomSVG from '../assets/svg/BorderBottomSVG.vue';
import vue from './knowledge/Vue.vue';
import react from './knowledge/React.vue';
import javascript from './knowledge/Javascript.vue';
import php from './knowledge/Php.vue';
import htmlCss from './knowledge/HtmlCss.vue';
import dynamoDBGraphQL from './knowledge/DynamoDBGraphQL.vue';
import jQuery from './knowledge/JQuery.vue';
import git from './knowledge/Git.vue';
import jira from './knowledge/Jira.vue';

import { ref, shallowRef, onMounted, onBeforeUnmount, type Component } from 'vue';

const knowledgePanel = shallowRef();
const circleCover = ref(false);
const onComponentEnter = ref(false);
const miniCirclesOff = ref(false);

const knowledgeContainer = ref();
const movingCircles = ref();
const intervalCircleMovement = ref(0);

const knowledge = shallowRef([
    { panel: vue, logo: "vue-logo.png" },
    { panel: react, logo: "react-logo.png" },
    { panel: javascript, logo: "javascript-logo.png" },
    { panel: php, logo: "php-logo.png" },
    { panel: htmlCss, logo: "CssHtml-logo.png" },
    { panel: dynamoDBGraphQL, logo: "DynamoDBGraphQL-logo.png" },
    { panel: jQuery, logo: "jQuery-logo.png" },
    { panel: git, logo: "git-logo.png" },
    { panel: jira, logo: "jira-logo.png" }
])

const getLogoImgUrl = (name: string) => {
    return new URL(`../img/${name}`, import.meta.url).href
}

const knowledgeSwap = (knowledgeItem: Component) => {
    circleCover.value = true;
    if (knowledgePanel.value != knowledgeItem) {
        miniCirclesOff.value = true;
        setTimeout(() => {
            knowledgePanel.value = knowledgeItem;
        }, 250);
    } else {
        knowledgePanel.value = undefined;
        setTimeout(() => {
            miniCirclesOff.value = false;
        },250)
        circleCover.value = false;
    }
}

const onLeave = () => {
    onComponentEnter.value = true;
}

const onEnter = () => {
    onComponentEnter.value = false;
}

onMounted(() => {
    const randomCircleMovement = () => {
        const width = knowledgeContainer.value.offsetWidth;
        const height = knowledgeContainer.value.offsetHeight;
        const x = Math.random() * width;
        const y = Math.random() * height;

        Array.from(movingCircles.value as HTMLDivElement[]).forEach(circle => {
            const top = (Math.floor(Math.random() * 10)) * 10;
            const left = (Math.floor(Math.random() * 10)) * 10;

            circle.style.top = `${top}%`;
            circle.style.left = `${left}%`;
        });
    }

    randomCircleMovement();
    intervalCircleMovement.value = window.setInterval(randomCircleMovement, 2500);
});

onBeforeUnmount(() => {
    clearInterval(intervalCircleMovement.value);
})
</script>