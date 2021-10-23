<template>
  <AppDrag
    :transfer-data="ingredient"
    :draggable="ingredient.count < MAX_INGREDIENTS_COUNT"
  >
    <span
      class="filling"
      :class="`filling--${INGREDIENTS_ARR[ingredient.name]}`"
    >
      {{ ingredient.name }}
    </span>
  </AppDrag>
</template>

<script>
import AppDrag from "@/common/components/AppDrag";
import { MAX_INGREDIENTS_COUNT } from "@/common/constants";
import { INGREDIENTS_ARR } from "@/common/constants";

export default {
  name: "Ingredient",
  components: {
    AppDrag,
  },
  props: {
    ingredient: {
      type: Object,
      required: true,
    },
  },
  data() {
    return {
      INGREDIENTS_ARR,
      MAX_INGREDIENTS_COUNT,
    };
  },
};
</script>

<style scoped></style>
