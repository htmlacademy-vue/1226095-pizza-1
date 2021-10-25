<template>
  <label :class="radioClass">
    <input
      type="radio"
      :name="name"
      class="visually-hidden"
      :checked="isChecked"
      :value="value"
      @change="$emit('editSelectValue', $event.target.value)"
    />
    <b v-if="boldText.length">{{ boldText }}</b>
    <span v-if="spanText.length">{{ spanText }}</span>
  </label>
</template>

<script>
export default {
  name: "RadioButton",
  props: {
    className: {
      type: String,
      required: true,
    },
    name: {
      type: String,
      required: true,
    },
    value: {
      type: Number,
      required: true,
    },
    checked: {
      type: Boolean,
      required: false,
    },
    boldText: {
      type: String,
      required: false,
      default: "",
    },
    spanText: {
      type: String,
      required: false,
      default: "",
    },
    selected: {
      type: Number,
      required: false,
    },
  },
  computed: {
    radioClass() {
      return this.className;
    },
    isChecked() {
      return this.selected === this.value;
    },
  },
};
</script>
