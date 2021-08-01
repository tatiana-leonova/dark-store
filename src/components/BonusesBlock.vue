<template>
  <ul class="bonuses">
    <li class="bonuses__item">
      <h3 class="bonuses__item-title bonuses__item-title--discounts">
        Скидка <span>1500 ₽</span>
      </h3>
      <p class="bonuses__item-text">
        <strong>–500 ₽</strong> &nbsp;на первые три заказа по&nbsp;промокоду NEW
      </p>
    </li>
    <span class="bonuses__plus">+</span>
    <li class="bonuses__item">
      <h3 class="bonuses__item-title bonuses__item-title--delivery">
        Бесплатная <span>доставка</span>
      </h3>
      <p class="bonuses__item-text">первого заказа</p>
    </li>
  </ul>
</template>

<script>
export default {
  name: "BonusesBlock",
};
</script>

<style lang="scss" scoped>
.bonuses {
  @include no-list;
  position: relative;
  padding: 0 10px;
  margin-bottom: 30px;

  @media (min-width: $width-xl) {
    display: flex;
    justify-content: space-between;
    flex-wrap: wrap;
    margin: 20px auto 50px auto;
    width: 900px;
  }

  &__item {
    position: relative;
    border: 1px solid $color_border;
    padding: 25px;
    text-align: center;
    max-width: 450px;
    margin: 20px auto 15px auto;

    @media (min-width: $width-xl) {
      width: 390px;
      text-align: left;
      padding: 35px 25px;
      margin: 0;
    }

    p {
      @include text(14px, 22px);

      @media (min-width: $width-xl) {
        @include text(16px, 24px);
      }
    }
  }

  &__item-title {
    position: relative;
    @include text(30px, 30px);
    font-weight: 700;
    letter-spacing: 0;
    padding-top: 90px;
    margin: 0;

    @media (min-width: $width-xl) {
      @include text(36px, 40px);
      padding: 0 0 0 110px;
    }

    span {
      color: $color_accent;
      @media (min-width: $width-xl) {
        display: block;
      }
    }

    &::after {
      position: absolute;
      display: block;
      content: "";
      top: 25px;
      left: calc(50% - 15px);
      width: 29px;
      height: 19px;
      background-repeat: no-repeat;

      @media (min-width: $width-xl) {
        top: 22px;
        left: 32px;
      }
    }

    &::before {
      position: absolute;
      display: block;
      content: "";
      top: 5px;
      left: calc(50% - 30px);
      width: 60px;
      height: 60px;
      border-radius: 50%;
      background-color: $color_accent;

      @media (min-width: $width-xl) {
        width: 70px;
        height: 70px;
        top: -3px;
        left: 10px;
      }
    }

    &--discounts {
      &::after {
        background-image: url("~@/assets/image/discounts.svg");
      }
    }

    &--delivery {
      &::after {
        left: calc(50% - 22px);
        width: 44px;
        height: 23px;
        background-image: url("~@/assets/image/delivery.svg");

        @media (min-width: $width-xl) {
          left: 22px;
        }
      }
    }
  }

  &__item-text {
    margin: 5px 0;
    @media (min-width: $width-xl) {
      padding: 0 0 0 110px;
    }
  }

  &__plus {
    display: block;
    @include text(36px, 46px);
    font-weight: 700;
    text-align: center;

    @media (min-width: $width-xl) {
      align-self: center;
    }
  }
}
</style>
