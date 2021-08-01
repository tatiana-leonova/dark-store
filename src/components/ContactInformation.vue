<template>
  <ul class="contacts">
    <li v-for="contact in contacts">
      <p class="contacts__city">
        {{ contact.city }}
      </p>
      <a
        class="contacts__phone"
        :href="'tel:' + contact.phone"
        aria-label="Позвонить"
      >
        {{ contact.phone | phoneFormats }}
      </a>
    </li>
  </ul>
</template>

<script>
export default {
  name: "ContactInformation",

  data() {
    return {
      contacts: [
        {
          city: "Москва",
          phone: "74957975777",
        },
        {
          city: "Санкт-Петербург",
          phone: "78123859955",
        },
      ],
    };
  },

  filters: {
    phoneFormats: (phone) => {
      return phone
        .replace(/[^0-9]/g, "")
        .replace(/(\d{1})(\d{3})(\d{3})(\d{2})(\d{2})/, "+$1 $2 $3-$4-$5");
    },
  },
};
</script>

<style lang="scss" scoped>
.contacts {
  @include no-list;
  padding: 15px 0 0 0;

  @media (min-width: $width-xl) {
    display: flex;
    flex-wrap: wrap;
  }

  li {
    margin-right: 40px;
    margin-bottom: 10px;

    @media (min-width: $width-xxl) {
      margin-right: 50px;
    }
  }

  &__city {
    @include text(14px, 22px);
    margin: 0;
  }

  &__phone {
    @include text(22px, 36px);
    font-weight: bold;
    color: $color_white;
    text-decoration: none;
    transition: all 0.5s;
    position: relative;
    padding-bottom: 7px;

    &:after,
    &:before {
      transition: all 0.5s;
    }

    &:after {
      position: absolute;
      bottom: 0;
      left: 0;
      right: 0;
      margin: auto;
      width: 0%;
      content: ".";
      color: transparent;
      background: #aaa;
      height: 2px;
    }

    &:hover:after {
      width: 100%;
    }

    @include hover-focus-active;
  }
}
</style>
