<template>
  <div class="main-page-view">
    <UICarousel autoplay class="carousel" :images="images.mainCarousel" alt="carousel-image" />
    <UIText class="text" color="#ff69b4" :tag="widthX > 480 ? HeaderSize.h1 : HeaderSize.h2">
      {{ Inscriptions.mainPageGreetingsTitle }}
    </UIText>
    <UIText class="text" :tag="widthX > 480 ? HeaderSize.h1 : HeaderSize.h2">
      {{ Inscriptions.mainPageGreetings }}
    </UIText>
    <MainPageProfileEntrance class="banner" />
    <UIText class="text" color="#ff69b4" :tag="widthX > 480 ? HeaderSize.h1 : HeaderSize.h2">
      {{ Inscriptions.mainPageMostPopular }}
    </UIText>
    <UICarousel
      :slides-per-view="3"
      :space-between="20"
      :loop="false"
      draggable
      class="bottom-carousel"
      :images="images.mostPopularProductsCarousel"
      alt="carousel-image"
    />
  </div>
</template>

<script lang="ts">
export default {
  name: 'MainPageView',
};
</script>

<script setup lang="ts">
import UICarousel from '@/components/ui/UICarousel.vue';
import { computed } from 'vue';
import { useMainPageStore } from '@/stores/main-page.store';
import MainPageProfileEntrance from '@/components/sections/main-page/MainPageProfileEntrance.vue';
import UIText from '@/components/ui/UIText.vue';
import { useWindowWidthWatcher } from '@/composables/useWindowWidthWatcher';
import { HeaderSize } from '@/helpers/enums/_text-styles.enum';
import { Inscriptions } from '@/helpers/enums/_inscriptions.enum';
import { MainPageImages } from '@/helpers/types/stores-types/_main-page-store.type';

const mainPageStore = useMainPageStore();
const images = computed<MainPageImages>(() => mainPageStore.images);
const { widthX } = useWindowWidthWatcher();
</script>

<style scoped lang="scss">
.spinner {
  display: flex;
  margin: 0 auto;
}
.main-page-view {
  background: white !important;
  padding: 15px;
  margin-top: 34px;
  .carousel {
    margin-top: 24px;
    margin-bottom: 36px;
  }
  .banner {
    margin-top: 36px;
    margin-bottom: 36px;
  }
  .bottom-carousel {
    margin-bottom: 36px;
  }
}
</style>
