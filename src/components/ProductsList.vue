<template>
  <div class="products-list">
    <div class="products-list__buttons">
      <base-select
        :options="filterOptions"
        :select="filterSelect"
      ></base-select>
    </div>
    <div class="products-list__cards">
      <product-card
        v-for="product in productsList"
        :key="product.name"
        :product="product"
      ></product-card>
    </div>
  </div>
</template>

<script>
import ProductCard from "./ProductCard.vue";
export default {
  name: "products-list",
  components: { ProductCard },
  data() {
    return {
      productsList: [
        {
          name: "Nikon D810",
          description:
            "Создайте новый шедевр с помощью безукоризненной фотокамеры Nikon D810. Эта универсальная фотокамера с разрешением 36,3 млн пикселей позволит снять все — от мельчайших текстур до быстро движущихся объектов.",
          cost: 10000,
          imageURL:
            "https://cdn.nikoneurope.com/imported/images/web/EU/products/digital-cameras/dslr/hero_ppdd_updated/nikon_dslr_d810_black_front--original.png",
        },
        {
          name: "black and silver vintage camera",
          description:
            "Создайте новый шедевр с помощью безукоризненной фотокамеры Nikon D810. Эта универсальная фотокамера с разрешением 36,3 млн пикселей позволит снять все — от мельчайших текстур до быстро движущихся объектов.",
          cost: 23000,
          imageURL:
            "https://images.unsplash.com/photo-1495121553079-4c61bcce1894?ixlib=rb-1.2.1&ixid=MnwxMjA3fDB8MHxwaG90by1wYWdlfHx8fGVufDB8fHx8&auto=format&fit=crop&w=381&q=80",
        },
        {
          name: "Камера-обскура",
          description:
            "простейший вид устройства, позволяющего получать оптическое изображение объектов. Представляет собой светонепроницаемый ящик с отверстием в одной из стенок и экраном (матовым стеклом или тонкой белой бумагой) на противоположной стене. Лучи света, проходя сквозь малое отверстие (диаметр которого зависит от «фокусного расстояния» камеры, приблизительно 0,1—5 мм), создают перевёрнутое изображение на экране.",
          cost: 123000,
          imageURL:
            "https://upload.wikimedia.org/wikipedia/commons/thumb/b/bc/Camera_obscura_2.jpg/1280px-Camera_obscura_2.jpg",
        },
        {
          name: "Polaroid Camera",
          description:
            "The tiny analog instant camera that’s portable, wearable, and take-anywhere-able.",
          cost: 500,
          imageURL:
            "https://i.pinimg.com/736x/be/dd/2c/bedd2cc3ab100935f1cd3d18ea053879--polaroid-one-step-vintage-cameras.jpg",
        },
      ],
      filterOptions: [
        { text: "По умолчанию", value: "default", selected: true },
        { text: "По возрастанию цены", value: "ascending", selected: false },
        { text: "По убыванию цены", value: "descending", selected: false },
      ],
      filterSelect: {
        name: "productFilter",
        id: "products-list-filter",
      },
    };
  },
};
</script>

<style lang="scss" scoped>
@import "@/scss/abstract/_abstract.scss";

.products-list {
  max-width: 100%;
}
.products-list__buttons {
  width: 100%;
  text-align: right;
  margin-bottom: 8px;
}
.products-list__cards {
  display: flex;
  flex-wrap: wrap;
  justify-content: space-between;
  padding-top: 8px;
  > * {
    flex-basis: 32%;
    margin-bottom: 16px;
  }
}
</style>
