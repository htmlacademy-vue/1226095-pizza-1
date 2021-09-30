<template>
  <label class="input">
    <span class="visually-hidden">Название пиццы</span>
    <input
      type="text"
      name="pizza_name"
      placeholder="Введите название пиццы"
    />
  </label>
</template>
<script>
export default {
  name: "RadioButton",
  props: {
    type: {
      type: String,
      required: true,
    },
    name: {
      type: String,
      required: true,
    },
    span: {
      type: String,
      required: true,
      default: "",
      hidden: true,
    },
    placeholder: {
      type: String,
      required: false,
      default: "",
    },
    required: {
      status: false,
    },
  },
};
</script>
