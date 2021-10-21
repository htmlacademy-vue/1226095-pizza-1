<template>
  <AppDrag :transfer-data="ingredient" :draggable="isDragAvailable">
    <span
      class="filling"
      :class="`filling--${ingredientsArr[ingredient.name]}`"
    >
      {{ ingredient.name }}
    </span>
  </AppDrag>
</template>

<script>
import AppDrag from "@/common/components/AppDrag";
import { MAX_INGREDIENTS_COUNT } from "@/common/constants";
const ingredientsArr = {
  Грибы: "mushrooms",
  Чеддер: "cheddar",
  Салями: "salami",
  Ветчина: "ham",
  Ананас: "ananas",
  Бекон: "bacon",
  Лук: "onion",
  Чили: "chile",
  Халапеньо: "jalapeno",
  Маслины: "olives",
  Томаты: "tomatoes",
  Лосось: "salmon",
  Моцарелла: "mozzarella",
  Пармезан: "parmesan",
  "Блю чиз": "blue_cheese",
};
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
    countIngredient: {
      type: Number,
      required: true,
    },
  },
  data() {
    return {
      ingredientsArr,
      MAX_INGREDIENTS_COUNT,
    };
  },
  methods: {
    isDragAvailable({ countIngredient }) {
      return countIngredient < MAX_INGREDIENTS_COUNT;
    },
  },
};
</script>

<style scoped></style>
