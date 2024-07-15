<template>
  <div class="h-100 overflow-hidden">
    <div class="main h-100" id="1">
      <div
        class="glitch"
        :class="isBlur && 'blur'"
        :data-text="text"
        @click="
          isBlur = true;
          text = 'Blured';
        "
      >
        {{ text }}
      </div>
    </div>
    <div class="main h-100" id="2">
      <img
        id="2"
        width="100%"
        height="100%"
        style="object-fit: cover"
        src="https://www.stellar-blade.com/resources/front/images/post_ms7/01.jpg"
      />
    </div>
    <div class="main py-6" id="3">Created by the one and only - Dym</div>
  </div>
</template>

<script>
export default {
  data() {
    return {
      isBlur: false,
      text: "Glitch Text",
      isActive: 1,
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
  },
  methods: {
    handleScroll(e) {
      switch (this.isActive) {
        case 1:
          if (e?.key == "ArrowDown" || e?.deltaY > 0) {
            document.getElementById("2").scrollIntoView({
              behavior: "smooth",
            });
            this.isActive = 2;
          }
          break;
        case 2:
          if (e?.key == "ArrowUp" || e?.deltaY < 0) {
            document.getElementById("1").scrollIntoView({
              behavior: "smooth",
            });
            this.isActive = 1;
          }
          if (e.key == "ArrowDown" || e?.deltaY > 0) {
            document.getElementById("3").scrollIntoView({
              behavior: "smooth",
            });
            this.isActive = 3;
          }
          break;
        case 3:
          if (e?.key == "ArrowUp" || e?.deltaY < 0) {
            document.getElementById("2").scrollIntoView({
              behavior: "smooth",
            });
            this.isActive = 2;
          }
          break;
      }
    },
  },
};
</script>

<style lang="scss" scoped>
.main {
  background-color: black;
  color: white;
  display: flex;
  align-items: center;
  justify-content: center;
}

.glitch {
  position: relative;
  font-size: 50px;
  font-family: "Lucida Sans", "Lucida Sans Regular", "Lucida Grande",
    "Lucida Sans Unicode", Geneva, Verdana, sans-serif;
  font-weight: bold;
  color: #ffffff;
  letter-spacing: 3px;
  z-index: 1;
}

.blur {
  animation: blur-it 0.6s both;
}

.glitch:before {
  content: attr(data-text);
  position: absolute;
  top: 0;
  left: -2px;
  width: 100%;
  color: 50px;
  background-color: #000000;
  overflow: hidden;
  clip: rect(0, 900px, 0, 0);
  animation: noise-before 5s infinite linear alternate-reverse;
}

.glitch:after {
  content: attr(data-text);
  position: absolute;
  top: 0;
  left: 2px;
  width: 100%;
  color: 50px;
  background-color: #000000;
  overflow: hidden;
  clip: rect(0, 900px, 0, 0);
  animation: noise-after 10s infinite linear alternate-reverse;
}

@keyframes noise-before {
  0% {
    clip: rect(61px, 9999px, 52px, 0);
  }
  5% {
    clip: rect(33px, 9999px, 144px, 0);
  }
  10% {
    clip: rect(121px, 9999px, 115px, 0);
  }
  15% {
    clip: rect(144px, 9999px, 162px, 0);
  }
  20% {
    clip: rect(62px, 9999px, 180px, 0);
  }
  25% {
    clip: rect(34px, 9999px, 42px, 0);
  }
  30% {
    clip: rect(147px, 9999px, 179px, 0);
  }
  35% {
    clip: rect(99px, 9999px, 63px, 0);
  }
  40% {
    clip: rect(188px, 9999px, 122px, 0);
  }
  45% {
    clip: rect(154px, 9999px, 14px, 0);
  }
  50% {
    clip: rect(63px, 9999px, 37px, 0);
  }
  55% {
    clip: rect(161px, 9999px, 147px, 0);
  }
  60% {
    clip: rect(109px, 9999px, 175px, 0);
  }
  65% {
    clip: rect(157px, 9999px, 88px, 0);
  }
  70% {
    clip: rect(173px, 9999px, 131px, 0);
  }
  75% {
    clip: rect(62px, 9999px, 70px, 0);
  }
  80% {
    clip: rect(24px, 9999px, 153px, 0);
  }
  85% {
    clip: rect(138px, 9999px, 40px, 0);
  }
  90% {
    clip: rect(79px, 9999px, 136px, 0);
  }
  95% {
    clip: rect(25px, 9999px, 34px, 0);
  }
  100% {
    clip: rect(173px, 9999px, 166px, 0);
  }
}

@keyframes noise-after {
  0% {
    clip: rect(26px, 9999px, 33px, 0);
  }
  5% {
    clip: rect(140px, 9999px, 198px, 0);
  }
  10% {
    clip: rect(184px, 9999px, 89px, 0);
  }
  15% {
    clip: rect(121px, 9999px, 6px, 0);
  }
  20% {
    clip: rect(181px, 9999px, 99px, 0);
  }
  25% {
    clip: rect(154px, 9999px, 133px, 0);
  }
  30% {
    clip: rect(134px, 9999px, 169px, 0);
  }
  35% {
    clip: rect(26px, 9999px, 187px, 0);
  }
  40% {
    clip: rect(147px, 9999px, 137px, 0);
  }
  45% {
    clip: rect(31px, 9999px, 52px, 0);
  }
  50% {
    clip: rect(191px, 9999px, 109px, 0);
  }
  55% {
    clip: rect(74px, 9999px, 54px, 0);
  }
  60% {
    clip: rect(145px, 9999px, 75px, 0);
  }
  65% {
    clip: rect(153px, 9999px, 198px, 0);
  }
  70% {
    clip: rect(99px, 9999px, 136px, 0);
  }
  75% {
    clip: rect(118px, 9999px, 192px, 0);
  }
  80% {
    clip: rect(1px, 9999px, 83px, 0);
  }
  85% {
    clip: rect(145px, 9999px, 98px, 0);
  }
  90% {
    clip: rect(121px, 9999px, 154px, 0);
  }
  95% {
    clip: rect(156px, 9999px, 44px, 0);
  }
  100% {
    clip: rect(67px, 9999px, 122px, 0);
  }
}

@keyframes blur-it {
  0% {
    filter: blur(0px);
    transform: translate(0);
  }
  20% {
    filter: blur(2px);
    transform: translate(-2px, 0px);
  }
  40% {
    filter: blur(4px);
    transform: translate(-5px, 0px);
  }
  60% {
    filter: blur(6px);
    transform: translate(8px, 0px);
  }
  80% {
    filter: blur(8px);
    transform: translate(10px, 0px);
  }
  to {
    filter: blur(0px);
    transform: translate(0);
  }
}
</style>
