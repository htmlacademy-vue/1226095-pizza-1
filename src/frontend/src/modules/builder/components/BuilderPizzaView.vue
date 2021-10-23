<template>
  <app-drop @drop="addIngredient">
    <div class="content__constructor">
      <div class="pizza pizza--foundation--big-tomato">
        <div class="pizza__wrapper">
          <template v-for="ingredient in selectedIngredients">
            <div
              v-for="index in ingredient.count"
              :key="`${index}-${ingredient.count}`"
              class="pizza__filling"
              :class="[
                `pizza__filling--${INGREDIENTS_ARR[ingredient.name]}`,
                ingredientIndexClass[index - 1],
              ]"
            />
          </template>
        </div>
      </div>
    </div>
  </app-drop>
</template>
<script>
import AppDrop from "@/common/components/AppDrop";
import { INGREDIENTS_ARR } from "@/common/constants";
import { MAX_INGREDIENTS_COUNT } from "@/common/constants";
export default {
  name: "BuilderPizzaView",
  components: {
    AppDrop,
  },
  props: {
    ingredientsList: {
      type: Array,
      required: true,
    },
  },
  data() {
    return {
      INGREDIENTS_ARR,
      MAX_INGREDIENTS_COUNT,
    };
  },
  computed: {
    selectedIngredients() {
      return this.ingredientsList.filter((item) => item.count > 0);
    },
    ingredientIndexClass() {
      return ["", "pizza__filling--second", "pizza__filling--third"];
    },
  },
  methods: {
    addIngredient(ingredient) {
      if (ingredient.count < MAX_INGREDIENTS_COUNT) {
        this.$emit("editIngredientCount", ingredient.id, ingredient.count + 1);
      }
    },
  },
};
</script>
