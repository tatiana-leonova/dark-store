<template>
  <li class="benefit">
    <img :src="require(`@/assets/image/benefits/${icon}`)" alt="" />
    <h3>{{ title }}</h3>
    <p>{{ text }}</p>
  </li>
</template>

<script>
export default {
  name: "BenefitItem",
  props: {
    icon: {
      type: String,
      required: true,
    },
    title: {
      type: String,
      required: true,
    },
    text: {
      type: String,
      required: true,
    },
  },
};
</script>

<style lang="scss" scoped>
.benefit {
  @include text(2.7vw, 4vw);
  padding: 20px 5px 15px 5px;
  background-color: $color_white;
  box-shadow: 0 0 20px rgba(230, 231, 235, 0.09);
  border-radius: 5px;
  width: 48%;
  margin-bottom: 10px;
  text-align: center;

  @media (min-width: $width-sm) {
    @include text(16px, 24px);
    border-radius: 10px;
    padding: 20px 12px 15px 12px;
    margin-bottom: 30px;
  }

  @media (min-width: $width-xl) {
    padding: 30px 20px 15px 20px;
    width: 31%;
  }

  h3 {
    @media (min-width: $width-xl) {
      padding-top: 10px;
    }
  }

  img {
    display: block;
    margin: 0 auto;
    height: 14vw;
    width: auto;

    @media (min-width: $width-sm) {
      height: 95px;
    }
  }

  @media (min-width: $width-md) {
    @include text(16px, 24px);
  }

  h3 {
    margin-bottom: 10px;
  }
}
</style>
