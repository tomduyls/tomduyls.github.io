<template>
  <div class="wrapper">
    <div class="marquee">
      <span> You spin me right round, baby. Like a record, baby. </span>
    </div>
    <div class="main h-screen d-flex flex-column" id="1">
      <div style="overflow: hidden">
        <div class="text text-in" style="font-size: 128px">HEHE</div>
      </div>
      <div style="overflow: hidden" class="hehe-in">
        <div class="text mt-16 text-in" style="font-size: 64px">13 12 2001</div>
      </div>
    </div>
    <div class="main h-screen position-relative" id="2">
      <!-- <img
        id="2"
        width="100%"
        height="100%"
        style="object-fit: cover"
        src="https://www.stellar-blade.com/resources/front/images/post_ms7/01.jpg"
      /> -->
      <div class="position-absolute bottom-0 left-0">
        <div
          class="w-100 text-center font-weight-bold text-uppercase bg-red"
          style="font-size: 24px"
        >
          Live Reaction
        </div>
        <img
          id="2"
          width="200px"
          height="200px"
          src="/public/very_angry.png"
          style="object-fit: contain"
        />
      </div>
    </div>
    <div class="main py-6" id="3">Created by the one and only - Dym</div>
  </div>
</template>

<script>
export default {
  data() {
    return {
      isBlur: false,
      isActive: 1,
      touchStart: undefined,
      touchEnd: undefined,
    };
  },
  watch: {},
  created() {},
  mounted() {
    window.addEventListener("wheel", (event) => {
      this.handleScroll(event);
    });
    window.addEventListener("keydown", (event) => {
      this.handleScroll(event);
    });
    window.addEventListener("touchstart", (event) => {
      this.touchStart = event.changedTouches[0].clientY;
    });
    window.addEventListener("touchend", (event) => {
      this.touchEnd = event.changedTouches[0].clientY;
      this.handleScroll(event);
    });
    // const observer = new IntersectionObserver((entries, observer) => {}, {
    //   threshold: 1,
    // });
  },
  methods: {
    handleScroll(e) {
      switch (this.isActive) {
        case 1:
          if (
            e?.key == "ArrowDown" ||
            e?.deltaY > 0 ||
            this.touchStart - 30 > this.touchEnd
          ) {
            document.getElementById("2").scrollIntoView({
              behavior: "smooth",
            });
            this.isActive = 2;
            this.handleResetTouch();
          }
          break;
        case 2:
          if (
            e?.key == "ArrowUp" ||
            e?.deltaY < 0 ||
            this.touchStart < this.touchEnd - 30
          ) {
            document.getElementById("1").scrollIntoView({
              behavior: "smooth",
            });
            this.isActive = 1;
            this.handleResetTouch();
          }
          if (
            e?.key == "ArrowDown" ||
            e?.deltaY > 0 ||
            this.touchStart - 30 > this.touchEnd
          ) {
            document.getElementById("3").scrollIntoView({
              behavior: "smooth",
            });
            this.isActive = 3;
            this.handleResetTouch();
          }
          break;
        case 3:
          if (
            e?.key == "ArrowUp" ||
            e?.deltaY < 0 ||
            this.touchStart < this.touchEnd - 30
          ) {
            document.getElementById("2").scrollIntoView({
              behavior: "smooth",
            });
            this.isActive = 2;
            this.handleResetTouch();
          }
          break;
        default:
          this.handleResetTouch();
          break;
      }
    },
    handleResetTouch() {
      this.touchStart = undefined;
      this.touchEnd = undefined;
    },
  },
};
</script>

<style lang="scss" scoped>
.wrapper {
  // background-image: url("/public/adam_pizurny.gif");
  background-size: cover;
  background-color: black;
  position: relative;
}

@keyframes marquee {
  0% {
    transform: translateX(50%);
  }
  100% {
    transform: translateX(-100%);
  }
}

.marquee {
  position: fixed;
  padding: 3px;
  width: 100vh;
  left: -44vh;
  top: 48.3vh;
  color: white;
  display: flex;
  align-items: center;
  justify-content: flex-start;
  -ms-transform: rotate(-90deg);
  transform: rotate(-90deg);
  overflow: hidden;
  span {
    will-change: transform;
    -webkit-transform: translateX(50%);
    -moz-transform: translateX(50%);
    -o-transform: translateX(50%);
    -ms-transform: translateX(50%);
    transform: translateX(50%);
    white-space: nowrap;
    width: 100vh;
    text-align: end;
    animation: marquee 13s linear infinite;
  }
}

.main {
  color: white;
  display: flex;
  align-items: center;
  justify-content: center;
}

@keyframes text-in {
  0% {
    transform: translateY(110%);
  }
  100% {
    transform: translateY(0%);
  }
}

.hehe-in {
  transition: ease-in-out 0.8s;
  &:hover {
    .text-in {
      transform: translateY(0%);
    }
  }
  .text-in {
    transition: all 1s;
    padding: 0.2em 0.1em;
    // animation: text-in 1s ease-out;
    transform: translateY(110%);
  }
}
</style>
