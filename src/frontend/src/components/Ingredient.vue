<template>
  <AppDrag :transfer-data="ingredient">
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
  },
  data() {
    return {
      ingredientsArr,
    };
  },
};
</script>

<style scoped></style>
