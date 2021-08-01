<template>
  <section class="purchases" id="purchases">
    <div class="container">
      <h2 class="is-hidden">Покупайте у&nbsp;нас!</h2>
      <bonuses-block></bonuses-block>
      <purchase-button class="purchases__button"></purchase-button>
    </div>
  </section>
</template>

<script>
import PurchaseButton from "@/components/PurchaseButton.vue";
import BonusesBlock from "@/components/BonusesBlock.vue";

export default {
  name: "PurchasesBlock",
  components: {
    "purchase-button": PurchaseButton,
    "bonuses-block": BonusesBlock,
  },
};
</script>

<style lang="scss" scoped>
.purchases {
  padding: 10px 0 80px 0;

  @media (min-width: $width-sm) {
    padding: 40px 0 80px 0;
  }

  @media (min-width: $width-xl) {
    padding: 40px 0 100px 0;
  }

  &__button {
    margin: 0 10px;
  }
}
</style>
