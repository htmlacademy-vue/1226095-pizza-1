<template>
  <div class="content__result">
    <p>{{ `Итого: ${currentPrice} ₽` }}</p>
    <Button :buttonText="`Готовьте!`" :disabled="currentPrice == 0" />
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
    currentPrice: {
      type: Number,
      required: true,
      default: 0,
    },
  },
};
</script>
