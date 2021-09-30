<template>
  <div :class="`content__` + cardId">
    <div class="sheet">
      <h2 class="title title--small sheet__title">
        <slot name="card-title"></slot>
      </h2>
      <div class="sheet__content" :class="cardId">
        <slot name="card-content"></slot>
      </div>
    </div>
  </div>
</template>
<script>
export default {
  name: "Card",
  props: {
    cardId: {
      type: String,
    },
  },
};
</script>
