<template>
  <footer class="page-footer">
    <div class="container">
      <logo-icon class="page-footer__logo">
      </logo-icon>
      <div class="page-footer__contact-wrapper">
        <contact-information
            class="page-footer__contact-information"
        ></contact-information>
        <social-media class="page-footer__social-media">
        </social-media>
      </div>
    </div>
  </footer>
</template>

<script>
import LogoIcon from "@/components/LogoIcon.vue";
import ContactInformation from "@/components/ContactInformation.vue";
import SocialMedia from "@/components/SocialMedia.vue";

export default {
  name: "PageFooter",

  components: {
    "logo-icon": LogoIcon,
    "contact-information": ContactInformation,
    "social-media": SocialMedia
  }
};
</script>

<style lang="scss" scoped>
.page-footer {
  padding: 45px 40px;
  color: $color_white;
  background-color: $color_bg_dark;

  @media (min-width: $width-xl) {
    padding: 45px 0;
  }

  &__logo {
    width: 130px;
    height: 37px;
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
