<template>
  <section class="first-block">
    <div class="first-block__wrapper">
      <div class="container">
        <logo-icon class="first-block__logo">
        </logo-icon>
        <div class="first-block__content">
          <h1>Что такое даркстор?</h1>
          <p>
            Это магазин-склад без покупателей. <br />
            Именно здесь, а&nbsp;не&nbsp;в&nbsp;розничном магазине собирают ваши
            заказы.
          </p>
        </div>
        <swipe-down
            class="first-block__swipe-down"
            :link="linkSwipe"
        ></swipe-down>
        <div></div>
      </div>
    </div>
  </section>
</template>

<script>
import LogoIcon from "@/components/LogoIcon.vue";
import SwipeDown from "@/components/SwipeDown.vue";

export default {
  name: "FirstScreen",
  components: {
    "logo-icon": LogoIcon,
    "swipe-down": SwipeDown
  },

  data() {
    return {
      linkSwipe: "#purchases"
    };
  }
};
</script>

<style lang="scss" scoped>
.first-block {
  background-color: $color_bg_light;

  &__wrapper {
    color: $color_white;
    padding: 40px 0;
    background-color: $color_bg_dark;
    background: linear-gradient(
            110.87deg,
            #293e42 43.41%,
            rgba(24, 60, 67, 0) 86.15%
    ),
    url("~@/assets/image/promo.jpg");
    background-repeat: no-repeat;
    background-size: cover;
    clip-path: ellipse(100% 70% at 50% 30%);

    @media (min-width: $width-xl) {
      padding: 60px 80px 30px;
    }
  }

  &__logo {
    display: block;
    width: 100px;
    height: 27px;
    margin: 0 auto 70px auto;

    @media (min-width: $width-md) {
      width: 150px;
      height: 41px;
      margin: 0 auto 85px 0;
    }

    @media (min-width: $width-xxl) {
      margin: 0 auto 120px 0;
    }
  }

  &__content {
    text-align: center;
    max-width: 500px;
    padding: 0 20px;
    margin: 0 auto;

    @media (min-width: $width-md) {
      text-align: left;
      margin: 0 auto 30px 0;
    }

    @media (min-width: $width-xl) {
      padding: 0;
      margin: 0 auto 20px 0;
    }

    @media (min-width: $width-xxl) {
      max-width: 620px;
      margin: 0 auto 40px 0;
    }

    h1 {
      @include text(28px, 38px);
      font-weight: 700;
      letter-spacing: 0.02em;
      text-transform: uppercase;
      margin-bottom: 10px;

      @media (min-width: $width-md) {
        @include text(40px, 44px);
      }

      @media (min-width: $width-xxl) {
        @include text(54px, 60px);
      }
    }

    p {
      @include text(16px, 22px);

      @media (min-width: $width-md) {
        @include text(20px, 32px);
      }

      @media (min-width: $width-xl) {
        width: 370px;
        margin-top: 10px;
      }

      @media (min-width: $width-xxl) {
        @include text(26px, 44px);
        width: 600px;
      }
    }
  }

  &__swipe-down {
    display: none;

    @media (min-width: $width-md) {
      display: flex;
      justify-content: center;
    }
  }
}
</style>
