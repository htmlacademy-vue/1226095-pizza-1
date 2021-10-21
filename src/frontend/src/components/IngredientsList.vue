<template>
  <ul class="ingredients__list">
    <li class="ingredients__item" v-for="item in ingredients" :key="item.id">
      <ingredient :ingredient="item" :countIngredient="0"></ingredient>
      <counter :className="`ingredients`" :count="count" @setCount="setCount">
      </counter>
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
      count: 0,
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
  methods: {
    setCount(count) {
      this.count = count;
    },
  },
};
</script>

<style scoped></style>
