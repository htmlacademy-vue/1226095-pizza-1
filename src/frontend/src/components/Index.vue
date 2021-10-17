<template>
  <form action="#" method="post">
    <div class="content__wrapper">
      <h1 class="title title--big">Конструктор пиццы</h1>
      <builder-dough-selector></builder-dough-selector>
      <builder-size-selector></builder-size-selector>
      <builder-ingredients-selector></builder-ingredients-selector>

      <div class="content__pizza">
        <div class="content__constructor">
          <div class="pizza pizza--foundation--big-tomato">
            <div class="pizza__wrapper">
              <div class="pizza__filling pizza__filling--ananas"></div>
              <div class="pizza__filling pizza__filling--bacon"></div>
              <div class="pizza__filling pizza__filling--cheddar"></div>
            </div>
          </div>
        </div>

        <div class="content__result">
          <p>Итого: 0 ₽</p>
          <button type="button" class="button" disabled>Готовьте!</button>
        </div>
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

export default {
  name: "Index",
  components: {
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
