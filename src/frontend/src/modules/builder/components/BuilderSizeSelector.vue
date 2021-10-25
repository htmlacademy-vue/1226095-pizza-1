<template>
  <Card :cardId="`diameter`">
    <template v-slot:card-title>Выберите тесто</template>
    <template v-slot:card-content>
      <RadioButton
        v-for="item in sizesList"
        :key="item.id"
        :name="`diameter`"
        :className="`diameter__input diameter__input--${SIZES_ARR[item.name]}`"
        :spanText="item.name"
        :value="item.id"
        :selected="selected"
        @editSelectValue="editSelectValue(item.id)"
      ></RadioButton>
    </template>
  </Card>
</template>
<script>
import Card from "@/components/Card";
import RadioButton from "@/components/RadioButton";
import pizza from "@/static/pizza";
import { SIZES_ARR } from "@/common/constants";

export default {
  name: "BuilderSizeSelector",
  components: {
    RadioButton,
    Card,
  },
  props: {
    sizesList: {
      type: Array,
      required: true,
    },
    selected: {
      type: Number,
      required: true,
    },
  },
  computed: {},
  data() {
    return {
      SIZES_ARR,
      pizza,
    };
  },
  methods: {
    editSelectValue(id) {
      this.$emit("editSelectCheckbox", id, `size`);
    },
  },
};
</script>
