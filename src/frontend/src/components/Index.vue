<template>
  <form action="#" method="post">
    <div class="content__wrapper">
      <h1 class="title title--big">Конструктор пиццы</h1>
      <builder-dough-selector
        :doughList="pizza.dough"
        :selected="selectedCheckbox.dough.id"
        @editSelectCheckbox="editSelectCheckbox"
      ></builder-dough-selector>
      <builder-size-selector
        :sizesList="pizza.sizes"
        :selected="selectedCheckbox.size.id"
        @editSelectCheckbox="editSelectCheckbox"
      ></builder-size-selector>
      <builder-ingredients-selector
        :saucesList="pizza.sauces"
        :selected="selectedCheckbox.sauce.id"
        :ingredientsList="ingredientsList"
        @editIngredientCount="editIngredientCount"
        @editSelectCheckbox="editSelectCheckbox"
      ></builder-ingredients-selector>
      <div class="content__pizza">
        <builder-pizza-view
          :ingredientsList="ingredientsList"
          :saucesList="pizza.sauces"
          :doughList="pizza.dough"
          :selected="selectedCheckbox"
          @editIngredientCount="editIngredientCount"
        ></builder-pizza-view>
        <builder-price-counter
          :ingredientsList="ingredientsList"
          :saucesList="pizza.sauces"
          :doughList="pizza.dough"
          :sizesList="pizza.sizes"
          :selected="selectedCheckbox"
        ></builder-price-counter>
      </div>
    </div>
  </form>
</template>

<script>
import pizza from "@/static/pizza";
import BuilderDoughSelector from "@/modules/builder/components/BuilderDoughSelector";
import BuilderSizeSelector from "@/modules/builder/components/BuilderSizeSelector";
import BuilderIngredientsSelector from "@/modules/builder/components/BuilderIngredientsSelector";
import BuilderPriceCounter from "@/modules/builder/components/BuilderPriceCounter";
import BuilderPizzaView from "@/modules/builder/components/BuilderPizzaView";

export default {
  name: "Index",
  components: {
    BuilderPizzaView,
    BuilderPriceCounter,
    BuilderIngredientsSelector,
    BuilderDoughSelector,
    BuilderSizeSelector,
  },
  data() {
    return {
      pizza,
      ingredientsList: pizza.ingredients.map((item) =>
        Object.assign({}, item, {
          count: 0,
        })
      ),
      selectedCheckbox: {
        size: {
          id: 1,
        },
        dough: {
          id: 1,
        },
        sauce: {
          id: 1,
        },
      },
    };
  },
  methods: {
    editIngredientCount(id, newCount) {
      this.ingredientsList.find((item) => item.id === id).count = newCount;
    },
    editSelectCheckbox(id, type) {
      switch (type) {
        case "size":
          this.selectedCheckbox.size.id = id;
          break;
        case "dough":
          this.selectedCheckbox.dough.id = id;
          break;
        case "sauce":
          this.selectedCheckbox.sauce.id = id;
          break;
      }
    },
  },
};
</script>
