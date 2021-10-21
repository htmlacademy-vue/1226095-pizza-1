<template>
  <div :class="[`counter counter--orange`, `${className}__counter`]">
    <button
      type="button"
      class="counter__button counter__button--minus"
      :class="count === 0 && 'counter__button--disabled'"
      :disabled="count === 0"
      @click="removeItem()"
    >
      <span class="visually-hidden">Меньше</span>
    </button>
    <input
      type="text"
      name="counter"
      class="counter__input"
      :value="count"
      @change="$emit('setCount', $event.target.value)"
    />
    <button
      type="button"
      class="counter__button counter__button--plus"
      :class="count >= MAX_INGREDIENTS_COUNT && 'counter__button--disabled'"
      :disabled="count >= MAX_INGREDIENTS_COUNT"
      @click="addItem()"
    >
      <span class="visually-hidden">Больше</span>
    </button>
  </div>
</template>

<script>
import { MAX_INGREDIENTS_COUNT } from "@/common/constants";
export default {
  name: "Counter",
  model: {
    prop: "count",
    event: "change",
  },
  props: {
    buttonPlusDisabled: {
      type: Boolean,
      required: false,
    },
    count: {
      type: Number,
      required: false,
      default: 0,
    },
    className: {
      type: String,
    },
  },
  data() {
    return {
      MAX_INGREDIENTS_COUNT,
      newCount: this.count,
    };
  },
  methods: {
    addItem() {
      if (this.count !== MAX_INGREDIENTS_COUNT) {
        this.newCount++;
        this.$emit("setCount", this.newCount);
      }
    },
    removeItem() {
      if (this.count > 0) {
        this.newCount--;
        this.$emit("setCount", this.newCount);
      }
    },
  },
};
</script>

<style></style>
