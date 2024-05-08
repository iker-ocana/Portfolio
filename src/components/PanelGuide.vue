<template>
    <div id="panel-guide">
        <span v-for="(breadcrumbTitle, panelIndex) in panelsBreadCrumb" class="panel-guide__item" @click="panelChange(panelIndex)">{{ breadcrumbTitle }}</span>
    </div>
</template>

<script setup lang="ts">
const panelsBreadCrumb = [
    'Inicio',
    'Sobre mi',
    'Experiencia',
    'Conocimientos'
]

const emit = defineEmits(['panelChange']);

const panelChange = (panel: Number) => {
    emit('panelChange', '', panel);
}
</script>