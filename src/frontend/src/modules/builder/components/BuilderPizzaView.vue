<template>
  <app-drop @drop="addIngredient">
    <div class="content__constructor">
      <div
        class="pizza"
        :class="`pizza--foundation--${pizzaDoughClass}-${pizzaSaucesClass}`"
      >
        <div class="pizza__wrapper">
          <template v-for="ingredient in selectedIngredients">
            <div
              v-for="index in ingredient.count"
              :key="`${index}-${ingredient.id}`"
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
import { DOUGH_SIZES } from "@/common/constants";
import { DOUGH_SIZES_CLASS } from "@/common/constants";
import { SAUCES_TYPE } from "@/common/constants";
export default {
  name: "BuilderPizzaView",
  components: {
    AppDrop,
  },
  props: {
    selected: {
      type: Object,
      required: true,
    },
    ingredientsList: {
      type: Array,
      required: true,
    },
    doughList: {
      type: Array,
      required: true,
    },
    saucesList: {
      type: Array,
      required: true,
    },
  },
  data() {
    return {
      INGREDIENTS_ARR,
      MAX_INGREDIENTS_COUNT,
      DOUGH_SIZES,
      DOUGH_SIZES_CLASS,
      SAUCES_TYPE,
    };
  },
  computed: {
    selectedIngredients() {
      return this.ingredientsList.filter((item) => item.count > 0);
    },
    ingredientIndexClass() {
      return ["", "pizza__filling--second", "pizza__filling--third"];
    },
    pizzaDoughClass() {
      return this.DOUGH_SIZES_CLASS[
        this.doughList.find((item) => item.id === this.selected.dough.id).name
      ];
    },
    pizzaSaucesClass() {
      return this.SAUCES_TYPE[
        this.saucesList.find((item) => item.id === this.selected.sauce.id).name
      ];
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
