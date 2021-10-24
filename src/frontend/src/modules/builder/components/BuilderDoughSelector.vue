<template>
  <Card :cardId="`dough`">
    <template v-slot:card-title>Выберите тесто</template>
    <template v-slot:card-content>
      <RadioButton
        v-for="item in doughList"
        :key="item.id"
        :name="`dought`"
        :className="`dough__input dough__input--${DOUGH_SIZES[item.name]}`"
        :boldText="item.name"
        :spanText="item.description"
        :selected="selected"
        :value="item.id"
        @editSelectValue="editSelectValue(item.id)"
      ></RadioButton>
    </template>
  </Card>
</template>
<script>
import Card from "@/components/Card";
import RadioButton from "@/components/RadioButton";
import pizza from "@/static/pizza";
import { DOUGH_SIZES } from "@/common/constants";
export default {
  name: "BuilderDoughSelector",
  components: {
    RadioButton,
    Card,
  },
  model: {
    prop: "selected",
    event: "change",
  },
  props: {
    doughList: {
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
      DOUGH_SIZES,
      pizza,
    };
  },
  methods: {
    editSelectValue(id) {
      this.$emit("editSelectCheckbox", id, `dough`);
    },
  },
};
</script>
