<template>
  <div class="app-layout">
    <div>
      <HeaderLayout></HeaderLayout>
    </div>
    <div class="content">
      <Index></Index>
    </div>
  </div>
</template>

<script>
import Index from "@/components/Index";
import HeaderLayout from "@/layouts/HeaderLayout";
export default {
  name: "AppLayout",
  components: {
    Index,
    HeaderLayout,
  },
};
</script>
