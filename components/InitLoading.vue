<template>
  <div
    class="d-flex align-center justify-center w-100 h-100"
    style="
      z-index: 50;
      position: fixed;
      top: 0;
      left: 0;
      background-color: black;
      color: white;
    "
    @click="$emit('loadDone')"
  >
    Loading...
  </div>
</template>

<script>
export default {
  props: {
    loading: Boolean,
  },
};
</script>

<style lang="scss" scoped></style>
