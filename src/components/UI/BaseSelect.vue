<template>
  <select
    v-bind="$attrs"
    class="select"
    :name="select.name"
    :id="select.id"
    :value="modelValue"
    @change="sendValue"
  >
    <option
      v-for="option in options"
      :key="option.value"
      :value="option.value"
      :selected="option.selected"
    >
      {{ option.text }}
    </option>
  </select>
</template>

<script>
export default {
  name: "base-select",
  emits: ["update:modelValue"],
  props: {
    modelValue: String,
    options: {
      type: Array,
      required: true,
    },
    select: {
      type: Object,
      required: true,
    },
  },
  methods: {
    sendValue(event) {
      this.$emit("update:modelValue", event.target.value);
    },
  },
};
</script>

<style lang="scss" scoped>
@import "@/scss/abstract/_abstract.scss";

.select {
  @extend %box-shadow-small;
  @include font($size: 12px, $height: calc(15 / 12));
  padding: 10px 16px 11px;
  background-color: $color-background;
  border: none;
  border-radius: 4px;
  color: $color-placeholders;
  &:focus {
    color: $color-text;
  }
}
</style>
