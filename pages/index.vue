<template>
  <div class="h-100 overflow-hidden">
    <Transition name="trans" mode="out-in">
      <InitLoading
        v-if="loading"
        :loading="loading"
        @load-done="loading = false"
      />
      <Content v-else />
    </Transition>
  </div>
</template>

<script setup lang="ts">
const nuxtApp = useNuxtApp();
const loading = ref(true);
nuxtApp.hook("page:start", () => {
  loading.value = true;
});
nuxtApp.hook("page:finish", () => {
  loading.value = false;
});
</script>

<style lang="scss" scoped>
.trans-enter-active,
.trans-leave-active {
  transition: all 0.4s;
}
.trans-enter-from,
.trans-leave-to {
  opacity: 0;
  filter: blur(1rem);
}
</style>
