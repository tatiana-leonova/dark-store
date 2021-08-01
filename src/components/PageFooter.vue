<template>
  <footer class="page-footer">
    <div class="container">
      <img
        class="page-footer__logo"
        src="@/assets/image/logo.svg"
        width="130"
        height="37"
        alt="logo Vprok"
      />
      <div class="page-footer__contact-wrapper">
        <contact-information
          class="page-footer__contact-information"
        ></contact-information>
        <social-media class="page-footer__social-media"></social-media>
      </div>
    </div>
  </footer>
</template>

<script>
import ContactInformation from "@/components/ContactInformation.vue";
import SocialMedia from "@/components/SocialMedia.vue";

export default {
  name: "PageFooter",

  components: {
    "contact-information": ContactInformation,
    "social-media": SocialMedia,
  },
};
</script>

<style lang="scss" scoped>
.page-footer {
  padding: 45px 40px;
  background-color: $color_bg_dark;
  color: $color_white;

  @media (min-width: $width-xl) {
    padding: 45px 0;
  }

  &__contact-wrapper {
    @media (min-width: $width-xl) {
      display: flex;
      justify-content: space-between;
      align-items: center;
    }
  }

  &__contact-information {
    @media (min-width: $width-xl) {
      max-width: 460px;
    }
  }

  &__social-media {
    @media (min-width: $width-xl) {
      max-width: 400px;
    }
  }
}
</style>
