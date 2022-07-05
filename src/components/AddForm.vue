<template>
  <div class="add-form">
    <h1 class="add-form__header">Добавление товара</h1>
    <form class="form add-form__form">
      <base-input :input="formInputs.name"></base-input>
      <base-textarea :textArea="formInputs.description"></base-textarea>
      <base-input :input="formInputs.image"></base-input>
      <base-input :input="formInputs.cost"></base-input>
      <base-button class="button" type="button" :disabled="true">
        Добавить товар
      </base-button>
    </form>
  </div>
</template>

<script>
export default {
  name: "add-form",
  data() {
    return {
      formInputs: {
        name: {
          type: "text",
          id: "product-name",
          name: "name",
          placeholder: "Введите наименование товара",
          required: true,
          label: {
            placeholder: "Наименование товара",
            for: "product-name",
          },
        },
        image: {
          type: "url",
          id: "product-image",
          name: "image",
          placeholder: "Введите ссылку",
          required: true,
          label: {
            placeholder: "Ссылка на изображение товара",
            for: "product-image",
          },
        },
        cost: {
          type: "number",
          id: "product-cost",
          name: "cost",
          placeholder: "Введите цену",
          required: true,
          label: {
            placeholder: "Цена товара",
            for: "product-cost",
          },
        },
        description: {
          type: "textArea",
          id: "product-description",
          name: "description",
          placeholder: "Введите описание товара",
          required: false,
          label: {
            placeholder: "Описание товара",
            for: "product-description",
          },
        },
      }
    };
  },
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
.form__text-area {
  height: 108px;
  width: 100%;
  resize: none;
}
</style>
