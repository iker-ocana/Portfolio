<template>
  <div id="portfolio">
    <header>
      <themeSelector />
      <PanelGuide @panelChange="interactivePanel" />
    </header>


    <div class="back-panel no-background">
      <picture>
        <img :src="imageURL" loading="lazy" @click="interactivePanel('backwards')" />
      </picture>
    </div>

    <main id="main-content">
      <Transition appear name="transition-component" mode="out-in">
        <component :is='resumeComponents[currentResumeComponent]'></component>
      </Transition>
    </main>

    <div class="next-panel no-background">
      <picture>
        <img :src="imageURL" loading="lazy" @click="interactivePanel('forward')" />
      </picture>
    </div>

    <FooterApp />
  </div>
</template>

<script setup lang="ts">
import PanelGuide from './components/PanelGuide.vue'
import themeSelector from './components/ThemeSelector.vue'
import firstPanel from '@/components/FirstPanel.vue'
import secondPanel from '@/components/SecondPanel.vue'
import thirdPanel from '@/components/ThirdPanel.vue'
import fourthPanel from '@/components/FourthPanel.vue'
import FooterApp from '@/components/Footer.vue'
import { ref, onMounted } from 'vue'

const resumeComponents = [
  firstPanel,
  secondPanel,
  thirdPanel,
  fourthPanel
]

const currentResumeComponent = ref(0)

const interactivePanel = (direction: String, panelNumber = 0) => {
  if (direction == 'forward' && currentResumeComponent.value < resumeComponents.length - 1) {
    currentResumeComponent.value += 1
  } else if (direction == 'backwards' && currentResumeComponent.value > 0) {
    currentResumeComponent.value -= 1
  } else {
    currentResumeComponent.value = panelNumber
  }
}

const darkArrow = new URL(`./img/next_img.png`, import.meta.url).href;
const whiteArrow = new URL(`./img/next_img_white.png`, import.meta.url).href;
const imageURL = ref(whiteArrow);
const mutationObserverRef = ref<MutationObserver | String>('');

onMounted(() => {
  mutationObserverRef.value = new MutationObserver((mutations) => {
    for (const mutation of mutations) {
      if (mutation.type === 'attributes' && mutation.attributeName === 'color-scheme') {
        if (mutation.oldValue !== undefined) {
          (mutation.target as HTMLElement).getAttribute(mutation.attributeName) == 'dark' ? imageURL.value = whiteArrow : imageURL.value = darkArrow;
        }
      }
    }
  });

  mutationObserverRef.value.observe(document.body, {
    attributes: true,
    attributeFilter: ['color-scheme'],
    attributeOldValue: true,
  });
});
</script>