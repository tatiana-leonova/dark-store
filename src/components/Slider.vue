<template>
  <div class="slider">
    <div ref="container" class="slider__container">
      <div class="slider__wrapper-outer">
        <div
          class="slider__wrapper"
          :style="{ transform: `translate3d(${currentPosition}px, 0, 0)` }"
        >
          <div
            v-for="(slide, index) in slides"
            :key="slide.id"
            ref="slide"
            class="slider__item"
          >
            <span class="slider__number">{{ index + 1 }}</span>
            <div
              class="slider__item-image"
              :style="{
                backgroundImage:
                  'url(' + require('@/assets/image/video/' + slide.img) + ')',
              }"
            ></div>
            <div class="slider__content">
              <h3 class="slider__title">{{ slide.title }}</h3>
              <p class="slider__text">{{ slide.text }}</p>
            </div>
          </div>
        </div>
      </div>
    </div>
    <div class="slider__arrow-wrapper">
      <button
        class="slider__arrow slider__arrow--right"
        @click.prevent="goPreviousSlide"
        aria-label="Прерыдущий слайд"
      ></button>
      <button
        class="slider__arrow slider__arrow--left"
        @click.prevent="goNextSlide"
        aria-label="Следующий слайд"
      ></button>
    </div>
  </div>
</template>

<script>
export default {
  name: "Slider",

  props: {
    slides: {
      type: Array,
      required: true,
    },
  },
  data: () => {
    return {
      currentIndex: 0,
      isMounted: false,
      startX: 0,
    };
  },
  computed: {
    currentPosition() {
      if (!this.isMounted) {
        return 0;
      } else {
        return -(this.$refs.container.offsetWidth * this.currentIndex);
      }
    },
  },
  mounted() {
    this.isMounted = true;

    this.$refs.container.addEventListener("touchstart", (event) => {
      this.startX = (event.touches || event.originalEvent.touches)[0].clientX;
    });

    this.$refs.container.addEventListener("touchmove", (event) => {
      if (!this.startX) return;

      const xDelta =
        this.startX - (event.touches || event.originalEvent.touches)[0].clientX;

      if (xDelta > 45) {
        this.goNextSlide();
        this.startX = null;
      } else if (xDelta < -45) {
        this.goPreviousSlide();
        this.startX = null;
      }
    });
  },
  methods: {
    goPreviousSlide() {
      this.currentIndex -= 1;

      if (this.currentIndex < 0) {
        this.currentIndex = this.$refs.slide.length - 1;
      }
    },

    goNextSlide() {
      this.currentIndex += 1;

      if (this.currentIndex > this.$refs.slide.length - 1) {
        this.currentIndex = 0;
      }
    },
  },
};
</script>

<style lang="scss" scoped>
.slider {
  position: relative;
  text-align: center;

  &__container {
    display: inline-block;
    vertical-align: top;
    width: 90vw;
    max-width: 450px;
    overflow: hidden;

    @media (min-width: $width-md) {
      max-width: 640px;
    }
  }

  &__wrapper {
    display: inline-block;
    vertical-align: top;
    white-space: nowrap;
    transition: transform 0.5s ease;
  }

  &__item {
    position: relative;
    display: inline-block;
    vertical-align: top;
    width: 90vw;
    max-width: 450px;
    padding: 0 20px;
    border-radius: 10px;
    background: $color_white;

    @media (min-width: $width-md) {
      max-width: 640px;
      padding: 0 10px;
    }
  }

  &__number {
    display: block;
    z-index: 1;
    position: absolute;
    top: 5px;
    left: 25px;
    @include text(16px, 22px);
    font-weight: 700;
    color: $color_accent;

    @media (min-width: $width-md) {
      @include text(22px, 32px);
      top: -2px;
      left: 57px;
    }

    &::before {
      content: "";
      position: absolute;
      top: -9px;
      left: -16px;
      width: 40px;
      height: 40px;
      border-radius: 50%;
      background-color: $color_white;
      z-index: -1;

      @media (min-width: $width-md) {
        top: -8px;
        left: -21px;
        width: 50px;
        height: 50px;
      }
    }
  }

  &__wrapper-outer {
    padding: 20px 0;
    background: $color_white;
    box-shadow: 0 0 40px rgba(0, 0, 0, 0.1);
    border-radius: 10px;

    @media (min-width: $width-md) {
      padding: 40px 0 0 0;
    }
  }

  &__item-image {
    display: inline-block;
    vertical-align: top;
    width: 90%;
    max-width: 450px;
    height: 160px;
    background: none no-repeat 50% 50%;
    background-size: cover;

    @media (min-width: $width-md) {
      max-width: 640px;
      height: 284px;
    }
  }

  &__content {
    white-space: normal;
    @include text(14px, 22px);

    @media (min-width: $width-md) {
      padding: 0 60px;
    }
  }

  &__title {
    @include text(14px, 22px);
    position: relative;
    color: $color_text;
    margin-top: 20px;

    @media (min-width: $width-md) {
      @include text(16px, 24px);
      margin: 30px 0 0 0;
    }
  }

  &__text {
    @media (min-width: $width-md) {
      @include text(16px, 24px);
      margin-top: 5px;
    }
  }

  &__arrow-wrapper {
    display: flex;
    justify-content: center;
    padding-left: 50px;
  }

  &__arrow {
    width: 20px;
    height: 20px;
    background-color: inherit;
    border: none;
    border-top: 3px solid $color_border;
    border-right: 3px solid $color_border;
    transition: 0.5s;
    cursor: pointer;
    margin-top: 40px;
    margin-right: 50px;


    @media (min-width: $width-xl) {
      width: 30px;
      height: 30px;
    }

    &:hover {
      opacity: 0.8;
      border-top: 3px solid $color_accent;
      border-right: 3px solid $color_accent;
    }
  }

  &__arrow--left {
    transform: rotate(45deg);

    @media (min-width: $width-md) {
      position: absolute;
      top: calc(50% - 45px);
      right: calc(50% - 415px);
    }
  }

  &__arrow--right {
    transform: rotate(-135deg);

    @media (min-width: $width-md) {
      position: absolute;
      top: calc(50% - 45px);
      left: calc(50% - 365px);
    }
  }
}
</style>
