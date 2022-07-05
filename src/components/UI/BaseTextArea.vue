<template>
  <label
    :class="{
      form__label_required: textArea.required,
    }"
    class="form__label"
    :for="textArea.label.for"
    >{{ textArea.label.placeholder }}
  </label>
  <textarea
    class="form__text-area"
    :name="textArea.name"
    :id="textArea.id"
    :placeholder="textArea.placeholder"
    :required="textArea.required"
  ></textarea>
</template>

<script>
export default {
  name: "base-textarea",
  props: {
    textArea: {
      type: Object,
      required: true,
    },
  },
};
</script>

<style lang="scss" scoped>
@import "@/scss/abstract/_abstract.scss";

.form__text-area {
  @extend %font-primary;
  @extend %box-shadow-small;
  @include font($size: 12px, $height: calc(15 / 12));
  margin-bottom: 16px;
  padding: 10px 16px 11px;
  background-color: $color-background;
  border: none;
  border-radius: 4px;
  height: 108px;
  width: 100%;
  resize: none;
  &::placeholder {
    color: $color-placeholders;
  }
}
</style>
