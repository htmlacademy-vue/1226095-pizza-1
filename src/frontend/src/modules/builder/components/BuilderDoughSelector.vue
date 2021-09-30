<template>
  <Card :cardId="`dough`">
    <template v-slot:card-title>Выберите тесто</template>
    <template v-slot:card-content>
      <RadioButton
        v-for="item in dough"
        :key="item.id"
        :name="`dought`"
        :className="`dough__input dough__input--${doughArr[item.name]}`"
        :boldText="item.name"
        :spanText="item.description"
        :value="`${doughArr[item.name]}`"
      ></RadioButton>
    </template>
  </Card>
</template>
<script>
import Card from "@/components/Card";
import RadioButton from "@/components/RadioButton";
import pizza from "@/static/pizza";

const doughArr = {
  Тонкое: "light",
  Толстое: "large",
};

export default {
  name: "BuilderDoughSelector",
  components: {
    RadioButton,
    Card,
  },
  props: {},
  data() {
    return {
      doughArr,
      pizza,
    };
  },
  computed: {
    dough() {
      return this.pizza.dough;
    },
  },
};
</script>
