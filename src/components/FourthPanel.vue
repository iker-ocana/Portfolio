<template>
    <div id="knowledge">
        <borderTopSVG />
        <section class="knowledge__title">
            <h2 class="text-centered bold">Conocimientos adquiridos a lo largo de mi experiencia laboral</h2>
        </section>

        <section id="knowledge__container">
            <div v-for="item in knowledge" class="item" @click="knowledgeSwap(item.panel)">
                <img :src="getLogoImgUrl(item.logo)" :alt="item.logo.split('.')[0]">
            </div>
        </section>

        <section class="knowledge__expand" ref="knowledgeContainer">
            <div class="circle" :class="{ 'circle_cover': circleCover }"></div>
            <div class="moving-circle" :class="{ 'moving-circle-opacity': miniCirclesOff }" v-for="circle in 6"
                ref="movingCircles"></div>
            <Transition appear name="transition-component" mode="out-in" @beforeLeave="onLeave" @beforeEnter="onEnter">
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

import { ref, shallowRef, onMounted, onBeforeUnmount, type Component, type Ref} from 'vue';

interface KnowledgeItem {
  panel: Component;
  logo: string;
}

const knowledgePanel: Component = shallowRef();
const circleCover = ref<boolean>(false);
const onComponentEnter = ref<boolean>(false);
const miniCirclesOff = ref<boolean>(false);

const knowledgeContainer= ref<HTMLElement>();
const movingCircles = ref<HTMLDivElement[]>([]);
const intervalCircleMovement = ref<number>(0);

const knowledge: Ref<KnowledgeItem[]> = shallowRef([
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

const getLogoImgUrl = (name: string): string => {
    return new URL(`../img/${name}`, import.meta.url).href
}

const knowledgeSwap = (knowledgeItem: Component): void => {
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

const onLeave = (): void => {
    onComponentEnter.value = true;
}

const onEnter = (): void => {
    onComponentEnter.value = false;
}

onMounted(() => {
    const randomCircleMovement = ():void => {
        const width = knowledgeContainer.value?.offsetWidth;
        const height = knowledgeContainer.value?.offsetHeight;

        movingCircles.value.forEach(circle => {
            const top = (Math.floor(Math.random() * 10)) * 10;
            const left = (Math.floor(Math.random() * 10)) * 10;

            circle.style.top = `${top}%`;
            circle.style.left = `${left}%`;
        });
    }

    intervalCircleMovement.value = window.setInterval(randomCircleMovement, 2500);
    randomCircleMovement();
});

onBeforeUnmount(() => {
    clearInterval(intervalCircleMovement.value);
})
</script>