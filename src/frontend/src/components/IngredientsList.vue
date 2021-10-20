<template>
  <ul class="ingredients__list">
    <li class="ingredients__item" v-for="item in ingredients" :key="item.id">
      <ingredient :ingredient="item"></ingredient>
      <counter :className="`ingredients`"></counter>
    </li>
  </ul>
</template>

<script>
import pizza from "@/static/pizza";
import ingredient from "@/components/Ingredient";
import Counter from "@/components/Counter";

export default {
  name: "IngredientsList",
  components: {
    ingredient,
    Counter,
  },
  props: {},
  data() {
    return {
      pizza,
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
