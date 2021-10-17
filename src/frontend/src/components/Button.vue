<template>
  <button type="button" class="button" :disabled="disabled">
    {{ buttonText }}
  </button>
</template>
<script>
export default {
  name: "Button",
  props: {
    buttonText: {
      type: String,
      required: true,
      default: "",
    },
    disabled: {
      type: Boolean,
      required: false,
      default: false,
    },
  },
};
</script>
