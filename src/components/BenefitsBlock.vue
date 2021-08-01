<template>
  <section class="benefits" id="benefits">
    <div class="container">
      <h2>Преимущества даркстора</h2>
      <ul>
        <benefit-item
          v-for="(benefit, index) in benefits"
          :icon="benefit.icon"
          :title="benefit.title"
          :text="benefit.text"
          :key="index"
        >
        </benefit-item>
      </ul>
    </div>
  </section>
</template>

<script>
import BenefitItem from "@/components/BenefitItem.vue";

export default {
  name: "BenefitsBlock",
  components: {
    "benefit-item": BenefitItem,
  },

  data() {
    return {
      benefits: [
        {
          icon: "benefit-1.svg",
          title: "Нет контакта с посторонними людьми",
          text: "Заказ формируется из товаров, до которых никто не дотрагивался, как это возможно на полках обычного магазина. Фрукты и овощи отбираются сборщиком вручную.",
        },
        {
          icon: "benefit-2.svg",
          title: "Заморозка 1 раз",
          text: "Продукты замораживаются однократно и поддерживаются в этом состоянии, пока не будут доставлены к вам.",
        },
        {
          icon: "benefit-3.svg",
          title: "Профессиональные морозильные камеры",
          text: "Товар хранится в промышленных холодильных и морозильных зонах с оптимальными температурными режимами для разных товаров: овощей, фруктов, масла и т. д.",
        },
        {
          icon: "benefit-4.svg",
          title: "Разделка мяса и рыбы под заказ",
          text: "Мясо и рыба разделываются непосредственно для вас, а при транспортировке хранятся в специальных боксах с низкой температурой.",
        },
        {
          icon: "benefit-5.svg",
          title: "Своя пекарня",
          text: "Знак «Печём сами» на карточках товаров означает, что мы привезём вам свежеиспечённый тёплый хлеб.",
        },
        {
          icon: "benefit-6.svg",
          title: "Работаем с 1995 года",
          text: "Мы занимаемся продуктами  с 1995 года — все процессы хранения и доставки отточены до мелочей.",
        },
      ],
    };
  },
};
</script>

<style lang="scss" scoped>
.benefits {
  background-color: $color_bg_light;
  padding: 35px 0;

  @media (min-width: $width-sm) {
    padding: 40px 30px;
  }

  @media (min-width: $width-xl) {
    padding: 60px 0 40px 0;
  }

  @media (min-width: $width-xxl) {
    padding: 90px 0 100px 0;
  }

  h2 {
    @media (min-width: $width-sm) {
      margin-bottom: 40px;
    }

    @media (min-width: $width-xxl) {
      margin-bottom: 55px;
    }
  }

  ul {
    @include no-list;
    display: flex;
    justify-content: space-between;
    flex-wrap: wrap;
  }
}
</style>
