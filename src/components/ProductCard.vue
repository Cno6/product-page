<template>
  <div @mouseenter="isHover = true" @mouseleave="isHover = false" class="card">
    <span @click="deleteCard" v-if="isHover" class="card__delete"></span>
    <img class="card__image" :src="product.imageURL" alt="Polaroid's Camera" />
    <div class="card__content">
      <h2 class="card__name">{{ product.name }}</h2>
      <p class="card__description">
        {{ product.description }}
      </p>
      <p class="card__cost">
        {{ Intl.NumberFormat("ru-RU").format(product.cost) }} руб.
      </p>
    </div>
  </div>
</template>

<script>
export default {
  name: "product-card",
  props: {
    product: {
      type: Object,
      required: true,
    },
  },
  data() {
    return {
      isHover: false,
    };
  },
  methods: {
    deleteCard() {
      this.$emit('remove', this.product)
    },
  },
};
</script>

<style lang="scss" scoped>
@import "../scss/abstract/_abstract.scss";

.card {
  @extend %box-shadow-big;
  position: relative;
  display: flex;
  flex-direction: column;
  border-radius: 4px;
  overflow: visible;
  background-color: $color-background;
  &:hover {
    cursor: pointer;
  }
}
.card__delete {
  background: url("@/assets/icons/delete.svg") no-repeat center;
  position: absolute;
  top: -8px;
  right: -8px;
  display: block;
  width: 32px;
  height: 32px;
  background-color: $color-additional;
  border-radius: 10px;
}
.card__image {
  width: 100%;
  overflow: hidden;
  object-fit: cover;
  height: 200px;
}
.card__content {
  display: flex;
  flex-direction: column;
  justify-content: space-between;
  width: 100%;
  padding: 16px 16px 24px;
  flex-grow: 1;
}
.card__name {
  @include font($size: 2rem, $height: calc(25 / 20), $weight: 600);
  margin-bottom: 16px;
  -webkit-line-clamp: 2;
  display: -webkit-box;
  -webkit-box-orient: vertical;
  overflow: hidden;
}
.card__description {
  margin-bottom: 32px;
  -webkit-line-clamp: 4;
  display: -webkit-box;
  -webkit-box-orient: vertical;
  overflow: hidden;
  flex-grow: 1;
}
.card__cost {
  @include font($size: 2.4rem, $height: calc(30 / 24), $weight: 600);
}
</style>
