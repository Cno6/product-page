<template>
  <div class="add-form">
    <h1 class="add-form__header">Добавление товара</h1>
    <form class="form add-form__form">
      <label class="form__label form__label_required" for="product-name"
        >Наименование товара</label
      >
      <input
        class="form__input"
        type="text"
        id="product-name"
        name="name"
        placeholder="Введите наименование товара"
        required
      />

      <label class="form__label" for="product-description"
        >Описание товара</label
      >
      <textarea
        class="form__text-area"
        name="description"
        id="product-description"
        cols="30"
        rows="10"
        placeholder="Введите описание товара"
      ></textarea>

      <label class="form__label form__label_required" for="product-image"
        >Ссылка на изображение товара</label
      >
      <input
        class="form__input"
        type="url"
        id="product-image"
        name="image"
        placeholder="Введите ссылку"
        required
      />

      <label class="form__label form__label_required" for="product-image"
        >Цена товара</label
      >
      <input
        class="form__input"
        type="number"
        id="product-image"
        name="image"
        placeholder="Введите цену"
        required
      />

      <base-button class="button" type="button" :disabled="true">
        Добавить товар
      </base-button>
    </form>
  </div>
</template>

<script>
export default {
  name: "add-form",
};
</script>

<style scoped lang="scss">
@import "../scss/abstract/_abstract.scss";
.add-form {
}
.add-form__header {
  @include font($size: 2.8rem, $height: calc(35 / 28), $weight: 600);
  margin-bottom: 16px;
}
.add-form__form {
  @extend %box-shadow-big;
  width: 332px;
  background-color: $color-background;
  border-radius: 4px;
  padding: 24px;
  display: flex;
  flex-direction: column;
  > :last-child {
    margin-top: 8px;
  }
}

.form {
}
.form__label {
  position: relative;
  @include font($size: 1rem, $height: calc(13 / 10), $spacing: -0.02em);
  margin-bottom: 4px;
  &_required::after {
    position: absolute;
    top: 0;
    content: "";
    display: inline-block;
    width: 4px;
    height: 4px;
    background-color: $color-additional;
    border-radius: 50%;
  }
}
.form__input,
.form__text-area {
  @extend %font-primary;
  @extend %box-shadow-small;
  @include font($size: 12px, $height: calc(15 / 12));
  margin-bottom: 16px;
  padding: 10px 16px 11px;
  background-color: $color-background;
  border: none;
  border-radius: 4px;
  &::placeholder {
    color: $color-placeholders;
  }
}
.form__input {
}
.form__text-area {
  height: 108px;
  width: 100%;
  resize: none;
}
</style>
