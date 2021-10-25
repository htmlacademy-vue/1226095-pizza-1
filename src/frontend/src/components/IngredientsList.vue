<template>
  <ul class="ingredients__list">
    <li
      class="ingredients__item"
      v-for="item in ingredientsList"
      :key="item.id"
    >
      <ingredient :ingredient="item"></ingredient>
      <counter
        :className="`ingredients`"
        :count="item.count"
        @setCount="(newCount) => setCount(item.id, newCount)"
      >
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
  props: {
    ingredientsList: {
      type: Array,
      required: true,
    },
  },
  data() {
    return {
      pizza,
      ingredients: [],
    };
  },
  methods: {
    setCount(id, count) {
      this.$emit("editIngredientCount", id, count);
    },
  },
};
</script>

<style scoped></style>
