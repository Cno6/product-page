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
    v-bind="$attrs"
    @input="sendData"
    class="form__input"
    :type="input.type"
    :id="input.id"
    :name="input.name"
    :placeholder="input.placeholder"
    :required="input.required"
    :value="modelValue"
  />
</template>

<script>
export default {
  name: "base-input",
  emits: ["update"],
  props: {
    modelValue: String,
    input: {
      type: Object,
      required: true,
    },
  },
  data() {
    return {
      value: "",
      name: this.$props.input.name,
    };
  },
  methods: {
    sendData(e) {
      this.value = e.target.value;
      this.$emit("update", e.target.value, this.name);
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
