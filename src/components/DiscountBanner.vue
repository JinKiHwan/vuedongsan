<template>
  <div class="discount">
    <h4>지금 결제하면 {{ discountPercent }}% 할인</h4>
  </div>
</template>

<script>
export default {
  name: 'DiscountBanner',

  props: {
    discountPercent: Number,
  },
};
</script>

<style></style>
