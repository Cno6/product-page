<template>
  <label
    :class="{
      form__label_required: input.required,
    }"
    class="form__label"
    :for="input.label.for"
    >{{ input.label.placeholder }}
  </label>
  <input
    class="form__input"
    :type="input.type"
    :id="input.id"
    :name="input.name"
    :placeholder="input.placeholder"
    :required="input.required"
  />
</template>

<script>
export default {
  name: "base-input",
  props: {
    input: {
      type: Object,
      required: true,
    },
  },
};
</script>

<style lang="scss" scoped>
@import "@/scss/abstract/_abstract.scss";

.form__input {
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
</style>
