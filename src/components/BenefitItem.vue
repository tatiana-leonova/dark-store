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
      required: true
    },
    title: {
      type: String,
      required: true
    },
    text: {
      type: String,
      required: true
    }
  }
};
</script>

<style lang="scss" scoped>
.benefit {
  width: 48%;
  @include text(2.7vw, 4vw);
  text-align: center;
  padding: 20px 5px 15px 5px;
  background-color: $color_white;
  border-radius: 5px;
  box-shadow: 0 0 20px rgba(230, 231, 235, 0.09);
  margin-bottom: 10px;

  @media (min-width: $width-sm) {
    @include text(16px, 24px);
    padding: 20px 12px 15px 12px;
    border-radius: 10px;
    margin-bottom: 30px;
  }

  @media (min-width: $width-xl) {
    width: 31%;
    padding: 30px 20px 15px 20px;
  }

  h3 {
    @media (min-width: $width-xl) {
      padding-top: 10px;
    }
  }

  img {
    display: block;
    height: 14vw;
    width: auto;
    margin: 0 auto;

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
