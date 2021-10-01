<template>
  <Card :cardId="`diameter`">
    <template v-slot:card-title>Выберите тесто</template>
    <template v-slot:card-content>
      <RadioButton
        v-for="item in size"
        :key="item.id"
        :name="`diameter`"
        :className="`diameter__input diameter__input--${sizeArr[item.name]}`"
        :spanText="item.name"
        :value="`${sizeArr[item.name]}`"
      ></RadioButton>
    </template>
  </Card>
</template>
<script>
import Card from "@/components/Card";
import RadioButton from "@/components/RadioButton";
import pizza from "@/static/pizza";

const sizeArr = {
  "23 см": "small",
  "32 см": "normal",
  "45 см": "big",
};

export default {
  name: "BuilderSizeSelector",
  components: {
    RadioButton,
    Card,
  },
  props: {},
  data() {
    return {
      sizeArr,
      pizza,
    };
  },
  computed: {
    size() {
      return this.pizza.sizes;
    },
  },
};
</script>
