<template>
  <div :class="[`counter counter--orange`, `${className}__counter`]">
    <button
      type="button"
      class="counter__button counter__button--minus"
      disabled
    >
      <span class="visually-hidden">Меньше</span>
    </button>
    <input type="text" name="counter" class="counter__input" :value="value" />
    <button type="button" class="counter__button counter__button--plus">
      <span class="visually-hidden">Больше</span>
    </button>
  </div>
</template>

<script>
export default {
  name: "Counter",
  props: {
    buttonPlusDisabled: {
      type: Boolean,
      required: false,
    },
    value: {
      type: Number,
      required: false,
      default: 0,
    },
    className: {
      type: String,
    },
  },
};
</script>

<style></style>
