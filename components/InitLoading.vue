<template>
  <div
    class="d-flex align-center justify-center w-100 h-100 loading"
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
    <span>L</span>
    <span>O</span>
    <span>A</span>
    <span>D</span>
    <span>I</span>
    <span>N</span>
    <span>G</span>
    <span>.</span>
    <span>.</span>
    <span>.</span>
  </div>
</template>

<script>
export default {
  props: {
    loading: Boolean,
  },
};
</script>

<style lang="scss" scoped>
.loading {
  span {
    font-size: 3rem;
    animation: loading 0.9s infinite alternate;
    @for $i from 1 through 9 {
      &:nth-child(#{$i + 1}) {
        animation-delay: #{$i * 0.1}s;
      }
    }
  }
}

@keyframes loading {
  0% {
    transform: scale(1);
  }
  100% {
    transform: scale(0.8);
  }
}
</style>
