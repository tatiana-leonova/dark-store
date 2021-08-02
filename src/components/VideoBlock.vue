<template>
  <section class="video-block">
    <div class="container">
      <h2>Взгляните на процесс сборки своими глазами</h2>
      <slider :slides="slides"> </slider>
    </div>
  </section>
</template>

<script>
import Slider from "@/components/Slider.vue";

export default {
  name: "VideoBlock",
  components: {
    slider: Slider,
  },
  data() {
    return {
      slides: [
        {
          id: "1",
          img: "video-1.jpg",
          title: "Привезём точно по списку",
          text: "Сборщик берëт с собой наручный терминал, на котором он видит весь список покупок для каждого заказа.",
        },
        {
          id: "2",
          img: "video-2.jpg",
          title: "Собираем быстро и эффективно",
          text: "Для улучшения эргономики пространства товары размещены от тяжëлых к лëгким, находящимся уже в конечной зоне упаковки.",
        },
        {
          id: "3",
          img: "video-3.jpg",
          title: "За свежесть и качество отвечаем",
          text: "Выделены специальные зоны, в том числе холодная и морозильная.",
        },
        {
          id: "4",
          img: "video-4.jpg",
          title: "Шампунь не положат рядом с рыбой",
          text: "Собираем и упаковываем ваш заказ с заботой: соблюдаем принципы товарного соседства и учитываем вес товара.",
        },
        {
          id: "5",
          img: "video-5.jpg",
          title: "Довезëм в сохранности даже яйца",
          text: "Бережно транспортируем контейнеры, фиксируя их стяжными ремнями. Системы охлаждения поддерживают температурный режим.",
        },
      ],
    };
  },
};
</script>

<style lang="scss" scoped>
.video-block {
  background-color: $color_bg_light;
  padding: 0 0 50px 0;
  margin: 0 auto;

  @media (min-width: $width-md) {
    padding: 0 0 80px 0;
  }

  h2 {
    margin: 0 auto 30px auto;
  }
}
</style>
