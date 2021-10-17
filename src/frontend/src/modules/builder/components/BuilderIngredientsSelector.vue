<template>
  <Card :cardId="`dough`">
    <template v-slot:card-title>Выберите ингредиенты</template>
    <template v-slot:card-content>
      <div class="ingredients__sauce">
        <p>Основной соус:</p>
        <label
          class="radio ingredients__input"
          v-for="item in sauces"
          :key="item.id"
        >
          <input type="radio" name="sauce" :value="item.id" checked />
          <span>{{ item.name }}</span>
        </label>
      </div>
      <div class="ingredients__filling">
        <p>Начинка:</p>
        <ingredients-list></ingredients-list>
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
  },
};
</script>
