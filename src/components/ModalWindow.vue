<template>
    <div class="modal">
      <div class="modal__wrapper">
        <div class="modal__container">
          <div v-if="!flag">
            <div class="modal__header">
              <slot name="header"> default header </slot>
            </div>
            <div class="modal__body">
              <div>
                <slot name="body"> </slot>
              </div>
              <slot name="footer"> </slot>
            </div>
          </div>
          <div v-else>
            <slot name="success"></slot>
          </div>
          <button
            class="modal__default-button"
            @click="$emit('close')"
            aria-label="Закрыть форму"
          >
            &#215;
          </button>
        </div>
      </div>
    </div>
</template>

<script>
export default {
  name: "ModalWindow",

  props: {
    flag: {
      type: Boolean,
      default: true,
      required: true,
    },
  },
};
</script>

<style lang="scss" scoped>
.modal {
  position: fixed;
  top: 0;
  left: 0;
  width: 100%;
  height: 100%;
  background-color: rgba(255, 255, 255, 0.9);
  z-index: 30;
  transition: opacity 0.8s ease;

  &__wrapper {
    position: absolute;
    z-index: 100;
    left: 50%;
    top: 50%;
    transform: translate(-50%, -50%);
  }

  &__container {
    position: relative;
    width: 290px;
    margin: 0 auto;
    padding: 40px;
    background-color: #fff;
    border-radius: 10px;
    box-shadow: 0 2px 8px rgba(0, 0, 0, 0.33);
    transition: all 0.8s ease;

    @media (min-width: $width-md) {
      width: 500px;
    }
  }

  &__header h3 {
    margin-top: 0;
    color: #42b983;
  }

  &__body {
    margin: 20px 0;
  }

  &__default-button {
    position: absolute;
    top: 15px;
    right: 20px;
    @include text(50px, 50px);
    border: none;
    background-color: inherit;
    transition: all 0.5s ease;
    cursor: pointer;

    &:hover,
    &:focus {
      color: $color_accent;
    }

    &:active {
      opacity: 0.5;
    }
  }
}
</style>
