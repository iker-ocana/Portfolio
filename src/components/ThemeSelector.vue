<template>
    <div id="theme-container">
        <p>Activar/Desactivar modo oscuro</p>
        <label class="theme-container__switch">
            <input type="checkbox" @click="toggleDarkMode()" checked>
            <span class="theme-container__ball round"></span>
        </label>
    </div>
</template>

<script setup lang="ts">

import { useDark, useToggle} from '@vueuse/core'

const darkMode = useDark({
    selector: 'body',
    attribute: 'color-scheme',
    valueDark: 'dark',
    valueLight: 'light'
})

const toggleDarkMode = useToggle(darkMode)
</script>