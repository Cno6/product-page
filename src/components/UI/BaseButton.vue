<template>
  <button class="button" type="button">
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
  &[disabled] {
    background-color: $color-button-disable;
  }
}
</style>
