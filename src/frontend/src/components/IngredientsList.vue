<template>
  <ul class="ingredients__list">
    <li class="ingredients__item" v-for="item in ingredients" :key="item.id">
      <span class="filling" :class="`filling--${ingredientsArr[item.name]}`">
        {{ item.name }}
      </span>
      <counter :className="`ingredients`"></counter>
    </li>
  </ul>
</template>

<script>
import Counter from "@/components/Counter";
import pizza from "@/static/pizza";

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
  name: "IngredientsList",
  components: {
    Counter,
  },
  props: {},
  data() {
    return {
      pizza,
      ingredientsArr,
    };
  },
  computed: {
    sauces() {
      return this.pizza.sauces;
    },
    ingredients() {
      return this.pizza.ingredients;
    },
  },
};
</script>

<style scoped></style>
