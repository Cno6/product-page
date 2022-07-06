<template>
  <button class="button">
    <slot></slot>
  </button>
</template>

<script>
export default {
  name: "base-button",
};
</script>

<style lang="scss" scoped>
@import "../../scss/abstract/_abstract.scss";

.button {
  @extend %font-additional;
  @include font(
    $size: 1.2,
    $height: calc(15 / 12),
    $weight: 600,
    $spacing: -0.02em
  );
  padding: 10px 16px 11px;
  border: none;
  border-radius: 10px;
  background-color: $color-button-active;
  color: #fff;
  transition: background-color .3s ease;
  &:hover {
    cursor: pointer;
    background-color: $color-button-hover;
  }
  &:active {
    // ТЕСТ
    background-color: red;
  }
  &[disabled] {
    color: $color-placeholders;
    background-color: $color-button-disable;
  }
}
</style>
