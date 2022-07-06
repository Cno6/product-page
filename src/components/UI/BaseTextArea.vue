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
  emits: ["update"],
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
