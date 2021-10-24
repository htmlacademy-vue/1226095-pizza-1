<template>
  <Card :cardId="`dough`">
    <template v-slot:card-title>Выберите ингредиенты</template>
    <template v-slot:card-content>
      <div class="ingredients__sauce">
        <p>Основной соус:</p>
        <label
          class="radio ingredients__input"
          v-for="item in saucesList"
          :key="item.id"
        >
          <input
            type="radio"
            name="sauce"
            :value="item.id"
            :checked="item.id === selected"
            @change="
              $emit(
                'editSelectCheckbox',
                parseInt($event.target.value),
                `sauce`
              )
            "
          />
          <span>{{ item.name }}</span>
        </label>
      </div>
      <div class="ingredients__filling">
        <p>Начинка:</p>
        <ingredients-list
          :ingredientsList="ingredientsList"
          @editIngredientCount="
            (id, newCount) => $emit(`editIngredientCount`, id, newCount)
          "
        ></ingredients-list>
      </div>
    </template>
  </Card>
</template>
<script>
import Card from "@/components/Card";
import pizza from "@/static/pizza";
import IngredientsList from "@/components/IngredientsList";

export default {
  name: "BuilderIngredientsSelector",
  components: {
    IngredientsList,
    Card,
  },
  props: {
    ingredientsList: {
      type: Array,
      required: true,
    },
    saucesList: {
      type: Array,
      required: true,
    },
    selected: {
      type: Number,
      required: true,
    },
  },
  data() {
    return {
      pizza,
    };
  },
};
</script>
