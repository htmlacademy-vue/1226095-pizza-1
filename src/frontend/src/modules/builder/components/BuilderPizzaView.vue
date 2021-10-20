<template>
  <app-drop @drop="addIngredient">
    <div class="content__constructor">
      <div class="pizza pizza--foundation--big-tomato">
        <div class="pizza__wrapper">
          <div class="pizza__filling pizza__filling--ananas"></div>
          <div class="pizza__filling pizza__filling--bacon"></div>
          <div class="pizza__filling pizza__filling--cheddar"></div>
        </div>
      </div>
    </div>
  </app-drop>
</template>
<script>
import AppDrop from "@/common/components/AppDrop";
export default {
  name: "BuilderPizzaView",
  components: {
    AppDrop,
  },
  methods: {
    addIngredient(ingredient) {
      console.log(ingredient);
    },
  },
};
</script>
