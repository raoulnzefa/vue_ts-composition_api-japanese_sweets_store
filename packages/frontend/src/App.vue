<template>
  <div class="container">
    <NMessageProvider>
      <NConfigProvider>
        <router-view />
      </NConfigProvider>
    </NMessageProvider>
  </div>
</template>

<script lang="ts">
import { defineComponent } from 'vue';

export default defineComponent({
  name: 'App',
});
</script>

<script setup lang="ts">
import { NConfigProvider, NMessageProvider } from 'naive-ui';
</script>

<style scoped lang="scss">
.container {
  background: #e0e0e0;
}
</style>
