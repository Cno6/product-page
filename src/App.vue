<template>
  <add-form @update:product="addProduct"></add-form>
  <products-list :product="product"></products-list>
</template>

<script>
import AddForm from "@/components/AddForm.vue";
import ProductsList from "@/components/ProductsList.vue";

export default {
  name: "App",
  components: {
    AddForm,
    ProductsList,
  },
  data() {
    return {
      product: {
        name: "",
        description: "",
        cost: 0,
        imageURL: "",
      },
    };
  },
  methods: {
    addProduct(newProduct) {
      this.product = {
        name: newProduct.name,
        description: newProduct.description,
        cost: newProduct.cost,
        imageURL: newProduct.imageURL,
      };
    },
  },
};
</script>

<style lang="scss">
@import "./scss/main.scss";
@import url("https://fonts.googleapis.com/css2?family=Inter:wght@600&family=Source+Sans+Pro:wght@400;600&display=swap");

#app {
  box-sizing: content-box;
  max-width: 1376px;
  padding: 30px;
  margin: auto;
  background-color: $color-background;
  display: flex;
  justify-content: center;
  gap: $gap;
  @include media-mobile-big {
    gap: $gap-small;
  }
}
</style>
