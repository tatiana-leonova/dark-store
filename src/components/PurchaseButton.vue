<template>
  <div class="purchase-modal">
    <button
      class="button"
      type="button"
      @click="showModal"
      aria-label="Перейти к заполнению формы"
    >
      К&nbsp;покупкам
    </button>
    <modal-window :flag="isFormSent" v-if="isShowModal" @close="closeModal">
      <template v-slot:header>
        <h2>Оформите заказ</h2>
      </template>
      <template v-slot:body>
        <div v-if="!isFormSent" class="purchase-modal__body">
          <label class="is-hidden" for="email"> Введите email </label>
          <input
            class="purchase-modal__input"
            :class="{ error: isEmailError }"
            type="email"
            id="email"
            v-model="email"
            ref="email"
            :placeholder="[emailPlaceholder]"
            @blur="isEmailBlur = true"
          />

          <span v-if="isEmailError" class="purchase-modal__text-error">
            Поле email заполнено неверно
          </span>
        </div>
      </template>
      <template v-slot:footer>
        <button
          class="purchase-modal__button button"
          type="button"
          @click.prevent.once="purchasesSubmit"
          aria-label="Отправить форму"
        >
          Отправить
        </button>
      </template>
      <template v-slot:success>
        <h2>Спасибо!</h2>
        <p class="purchase-modal__success-text">Форма успешно отправлена</p>
      </template>
    </modal-window>
  </div>
</template>

<script>
import ModalWindow from "@/components/ModalWindow.vue";

export default {
  name: "PurchaseButton",
  components: {
    "modal-window": ModalWindow,
  },

  data() {
    return {
      isShowModal: false,
      isFormSent: false,
      isEmailBlur: false,
      email: "",
      emailPlaceholder: "Введите email",
      emailRegex:
        /^(([^<>()\[\]\\.,;:\s@"]+(\.[^<>()\[\]\\.,;:\s@"]+)*)|(".+"))@((\[[0-9]{1,3}\.[0-9]{1,3}\.[0-9]{1,3}\.[0-9]{1,3}])|(([a-zA-Z\-0-9]+\.)+[a-zA-Z]{2,24}))$/,
    };
  },

  computed: {
    isEmailValid() {
      return this.emailRegex.test(this.email);
    },

    isEmailError() {
      return !this.isEmailValid && this.isEmailBlur;
    },
  },
  methods: {
    showModal() {
      this.isShowModal = true;
      setTimeout(() => {
        this.$nextTick(() => this.$refs.email.focus());
      }, 100);
    },

    purchasesSubmit() {
      if (!this.isEmailValid) {
        return;
      }
      setTimeout(() => {
        this.isFormSent = true;
        console.log("Email: " + this.email);
      }, 500);
    },

    closeModal() {
      this.isEmailBlur = false;
      this.isShowModal = false;
      this.isFormSent = false;
      this.email = "";
    },
  },
};
</script>

<style lang="scss" scoped>
.purchase-modal {
  position: relative;

  &__input {
    width: 100%;
    height: 70px;
    border: 2px solid $color_border;
    border-radius: 10px;
    transition: all 0.5s ease;
    margin-bottom: 10px;
    outline: none;
    @include text(20px, 32px);
    color: $color_text;
    padding: 0 20px;
    opacity: 1;

    &::placeholder {
      color: $color_text;
      opacity: 1;
    }

    &:hover,
    &:focus,
    &:active {
      border: 2px solid $color_border;
    }
  }

  &__button {
    max-width: 100%;
  }

  &__text-error {
    position: absolute;
    bottom: -10px;
    left: 0;
    @include text(14px, 24px);
    color: $color_error;
  }

  &__body {
    position: relative;
    margin-bottom: 30px;
  }

  &__success-text {
    text-align: center;
    @include text(30px, 30px);
    margin: 0;
  }
}

.error {
  border-color: $color_error;
}
</style>
