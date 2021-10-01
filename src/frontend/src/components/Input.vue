<template>
  <label class="input">
    <span :class="{ spanHidden: 'visually-hidden'}">{{span}}</span>
    <input
      :type="type"
      :name="name"
      :placeholder="placeholder"
      :required="required"
    />
  </label>
</template>
<script>
export default {
  name: "Input",
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
    },
    spanHidden: {
      type: Boolean,
      required: true
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
