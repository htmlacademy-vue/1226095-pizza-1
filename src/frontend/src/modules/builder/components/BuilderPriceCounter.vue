<template>
  <div class="content__result">
    <p>{{ `Итого: ${currentPrice} ₽` }}</p>
    <Button :buttonText="`Готовьте!`" :disabled="currentPrice === 0" />
  </div>
</template>

<script>
import Button from "@/components/Button";
export default {
  name: "BuilderPriceCounter",
  components: {
    Button,
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
    sizesList: {
      type: Array,
      required: true,
    },
  },
  data() {
    return {};
  },
  computed: {
    selectedIngredients() {
      return this.ingredientsList.filter((item) => item.count > 0);
    },
    selectedSauce() {
      return this.saucesList.find((item) => item.id === this.selected.sauce.id);
    },
    selectedSize() {
      return this.sizesList.find((item) => item.id === this.selected.size.id);
    },
    selectedDough() {
      return this.doughList.find((item) => item.id === this.selected.dough.id);
    },
    currentPrice() {
      return (
        this.selectedSize.multiplier *
        (this.selectedDough.price +
          this.selectedSauce.price +
          this.selectedIngredients.reduce((acc, item) => {
            return (acc + item.price) * item.count;
          }, 0))
      );
    },
  },
  methods: {},
};
</script>
