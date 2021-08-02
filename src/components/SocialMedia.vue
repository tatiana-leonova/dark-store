<template>
  <ul class="social-media">
    <li v-for="item in socialMedia" :key="item.name">
      <a
          :href="item.link"
          aria-label="Перейти на страницу соцсети"
          target="_blank"
      >
        <img
            :src="require(`@/assets/image/social/${item.icon}`)"
            :alt="item.name"
        />
      </a>
    </li>
  </ul>
</template>

<script>
export default {
  name: "SocialMedia",
  data() {
    return {
      socialMedia: [
        {
          name: "facebook",
          link: "https://www.facebook.com/vprokru/",
          icon: "facebook.svg"
        },
        {
          name: "вконтакте",
          link: "https://vk.com/vprokru",
          icon: "vk.svg"
        },
        {
          name: "instagram",
          link: "https://www.instagram.com/vprokru/",
          icon: "instagram.svg"
        },
        {
          name: "одноклассники",
          link: "https://ok.ru/group/57911797088280",
          icon: "ok.svg"
        }
      ]
    };
  }
};
</script>

<style lang="scss" scoped>
.social-media {
  display: flex;
  flex-wrap: wrap;
  align-items: center;
  @include no-list;

  li {
    margin-bottom: 10px;
    margin-right: 40px;

    a {
      transition: all 0.5s;

      @include hover-focus-active;
    }
  }
}
</style>
