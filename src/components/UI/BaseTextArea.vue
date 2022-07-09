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
    v-bind="$attrs"
    class="form__text-area"
    :name="textArea.name"
    :id="textArea.id"
    :placeholder="textArea.placeholder"
    :required="textArea.required"
    :value="modelValue"
    @input="sendData"
  ></textarea>
</template>

<script>
export default {
  name: "base-textarea",
  emits: ["update:modelValue"],
  props: {
    modelValue: String,
    textArea: {
      type: Object,
      required: true,
    },
  },
  data() {
    return {
      name: this.$props.textArea.name,
    };
  },
  methods: {
    sendData(event) {
      this.$emit("update:modelValue", event.target.value);
    },
  },
};
</script>

<style lang="scss" scoped>
@import "@/scss/abstract/_abstract.scss";

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
