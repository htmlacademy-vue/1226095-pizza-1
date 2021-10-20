<template>
  <form action="#" method="post">
    <div class="content__wrapper">
      <h1 class="title title--big">Конструктор пиццы</h1>
      <builder-dough-selector></builder-dough-selector>
      <builder-size-selector></builder-size-selector>
      <builder-ingredients-selector></builder-ingredients-selector>
      <div class="content__pizza">
        <builder-pizza-view></builder-pizza-view>
        <builder-price-counter :currentPrice="0"></builder-price-counter>
      </div>
    </div>
  </form>
</template>

<script>
import misc from "@/static/misc";
import pizza from "@/static/pizza";
import user from "@/static/user";
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
      misc,
      pizza,
      user,
    };
  },
  computed: {
    dough() {
      return this.pizza.dough;
    },
    size() {
      return this.pizza.sizes;
    },
  },
};
</script>
