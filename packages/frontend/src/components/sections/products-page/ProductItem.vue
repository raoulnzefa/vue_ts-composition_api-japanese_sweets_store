<template>
  <NCard
    hoverable
    @click.prevent="$router.push({ name: PageName.productById, params: { productId: product.id } })"
  >
    <ProductCover class="cover" :image="product.image" />
    <div class="title">
      <UIText class="title" tag="NH6">{{ product.title }}</UIText>
    </div>
    <div class="cost">
      <ProductCost :cost="product.cost" :sale="product.sale" />
    </div>
  </NCard>
</template>

<script lang="ts">
import { defineComponent } from 'vue';

export default defineComponent({
  name: 'ProductItem',
});
</script>

<script setup lang="ts">
import { NCard } from 'naive-ui';
import { defineProps, PropType } from 'vue';
import UIText from '@/components/ui/UIText.vue';
import { Product } from '@/helpers/types/stores-types/_products-page-store.type';
import { PageName } from '@/helpers/enums/_pages.enum';
import ProductCost from '@/components/sections/common/ProductCost.vue';
import ProductCover from '@/components/sections/common/ProductCover.vue';

defineProps({
  product: {
    type: Object as PropType<Product>,
    default: () => ({}),
  },
});
</script>

<style scoped lang="scss">
@media (max-width: 599px) {
  .n-card {
    margin-bottom: 15px;
    display: flex;
    cursor: pointer;
    width: 85vw;
    height: 50vh;
    .cover {
      width: 100%;
      height: 65%;
      background-size: cover;
      background-position: center;
    }
    .title {
      margin-top: 30px;
      width: 100%;
      height: 25%;
    }
    .cost {
      margin-top: -15px;
      height: 10%;
      flex-grow: 1;
      .with-sale {
        display: flex;
        justify-content: space-around;
        width: 100px;
        margin: 0 auto;
        align-self: center;
      }
    }
  }
}
@media (min-width: 600px) and (max-width: 799px) {
  .n-card {
    display: flex;
    cursor: pointer;
    width: 260px;
    height: 320px;
    .cover {
      width: 100%;
      height: 65%;
      background-size: cover;
      background-position: center;
    }
    .title {
      width: 100%;
      height: 25%;
    }
    .cost {
      margin-top: 8px;
      height: 10%;
      flex-grow: 1;
      .with-sale {
        display: flex;
        justify-content: space-around;
        width: 100px;
        margin: 0 auto;
        align-self: center;
      }
    }
  }
}
@media (min-width: 800px) and (max-width: 1119px) {
  .n-card {
    display: flex;
    cursor: pointer;
    width: 250px;
    height: 320px;
    .cover {
      width: 100%;
      height: 65%;
      background-size: cover;
      background-position: center;
    }
    .title {
      width: 100%;
      height: 25%;
    }
    .cost {
      margin-top: 8px;
      height: 10%;
      flex-grow: 1;
      .with-sale {
        display: flex;
        justify-content: space-around;
        width: 100px;
        margin: 0 auto;
        align-self: center;
      }
    }
  }
}
@media (min-width: 1120px) and (max-width: 1399px) {
  .n-card {
    display: flex;
    cursor: pointer;
    width: 230px;
    height: 300px;
    .cover {
      width: 100%;
      height: 65%;
      background-size: cover;
      background-position: center;
    }
    .title {
      width: 100%;
      height: 25%;
    }
    .cost {
      margin-top: 8px;
      height: 10%;
      flex-grow: 1;
      .with-sale {
        display: flex;
        justify-content: space-around;
        width: 100px;
        margin: 0 auto;
        align-self: center;
      }
    }
  }
}
@media (min-width: 1400px) {
  .n-card {
    display: flex;
    cursor: pointer;
    width: 250px;
    height: 310px;
    .cover {
      width: 100%;
      height: 65%;
      background-size: cover;
      background-position: center;
    }
    .title {
      width: 100%;
      height: 25%;
    }
    .cost {
      height: 10%;
      flex-grow: 1;
      margin-top: 10px;
      .with-sale {
        display: flex;
        justify-content: space-around;
        width: 100px;
        margin: 0 auto;
        align-self: center;
      }
    }
  }
}
</style>
