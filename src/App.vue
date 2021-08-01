<template>
  <div id="app">
    <main class="main-page">
      <first-block></first-block>
      <benefits-block></benefits-block>
      <video-block></video-block>
      <purchases-block></purchases-block>
    </main>
    <page-footer></page-footer>
    <button-scroll-top></button-scroll-top>
  </div>
</template>

<script>
import FirstBlock from "./components/FirstBlock.vue";
import BenefitsBlock from "./components/BenefitsBlock.vue";
import VideoBlock from "./components/VideoBlock.vue";
import PurchasesBlock from "./components/PurchasesBlock.vue";
import PageFooter from "./components/PageFooter.vue";
import ButtonScrollTop from "./components/ButtonScrollTop.vue";

export default {
  name: "App",
  components: {
    "first-block": FirstBlock,
    "benefits-block": BenefitsBlock,
    "video-block": VideoBlock,
    "purchases-block": PurchasesBlock,
    "page-footer": PageFooter,
    "button-scroll-top": ButtonScrollTop,
  },
};
</script>

<style lang="scss">
.main-page {
}
</style>
