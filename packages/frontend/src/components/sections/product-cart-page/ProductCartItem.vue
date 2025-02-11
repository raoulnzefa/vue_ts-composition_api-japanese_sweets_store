<template>
  <div class="product-cart-item">
    <div class="title-wrap" @click="goTo">
      <ProductCover class="cover" :image="cloneItem.product.image" />
      <div class="title">
        <UIText tag="NH2">{{ cloneItem.product.title }}</UIText>
      </div>
    </div>
    <div class="info-wrap">
      <NInputNumber
        :min="0"
        :max="10"
        :value="cloneItem.amount"
        @update:value="updateItem"
        bordered
        class="count"
      />
      <NButton @click="updateItem(0)" class="remove-btn" strong secondary circle type="error">
        <template #icon>
          <NIcon><AddCircleOutlineTwotone style="transform: rotate(45deg)" /></NIcon>
        </template>
      </NButton>
      <div class="price">
        <ProductCost
          :cost="item.product.cost"
          :sale="item.product.sale"
          :amount="item.amount"
          font-size="NH3"
        />
      </div>
    </div>
  </div>
</template>

<script lang="ts">
import { defineComponent } from 'vue';

export default defineComponent({
  name: 'ProductCartItem',
});
</script>

<script setup lang="ts">
import { CartProductType } from '@/helpers/types/stores-types/_product-cart-store.type';
import { PropType, defineProps, computed, defineEmits } from 'vue';
import ProductCover from '@/components/sections/common/ProductCover.vue';
import UIText from '@/components/ui/UIText.vue';
import { NInputNumber, NButton, NIcon } from 'naive-ui';
import { cloneDeep } from 'lodash';
import { AddCircleOutlineTwotone } from '@vicons/material';
import ProductCost from '@/components/sections/common/ProductCost.vue';
import { PageName } from '@/helpers/enums/_pages.enum';
import { useRouter } from 'vue-router';

const router = useRouter();
const emit = defineEmits(['custom:updateItem']);

const props = defineProps({
  item: {
    type: Object as PropType<CartProductType>,
    required: false,
    default: () => ({}),
  },
});
const cloneItem = computed(() => cloneDeep(props.item));
const updateItem = (e: number): void => {
  cloneItem.value.amount = e;
  emit('custom:updateItem', cloneItem.value);
};
const goTo = (): void => {
  router.push({ name: PageName.productById, params: { productId: props.item.product?.id } });
};
</script>

<style scoped lang="scss">
@media (max-width: 499px) {
}
@media (min-width: 500px) and (max-width: 799px) {
}
@media (min-width: 800px) and (max-width: 1019px) {
}
@media (min-width: 1020px) and (max-width: 1399px) {
  .product-cart-item {
    display: flex;
    .cover {
      width: 100px;
      height: 100px;
    }
  }
}
@media (min-width: 1400px) {
  .product-cart-item {
    width: 100%;
    display: flex;
    align-items: center;
    .title-wrap {
      display: flex;
      align-items: center;
      width: 70%;
      height: 100%;
      cursor: pointer;
      .cover {
        width: 100px;
        height: 100px;
        margin-right: 10px;
      }
      .title {
        margin-top: 15px;
        margin-right: 20px;
      }
    }
    .info-wrap {
      display: flex;
      justify-content: space-around;
      align-items: center;
      .remove-btn {
        margin-left: 10px;
        margin-right: 10px;
      }
      .price {
        margin-top: 20px;
      }
    }
  }
  .count {
    width: 80px;
  }
}
</style>
