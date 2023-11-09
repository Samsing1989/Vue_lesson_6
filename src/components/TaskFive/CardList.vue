<template>
  <div class="list">
    <card-product
      v-for="prod in productData"
      :key="prod.id"
      :card-product="prod"
    />
  </div>
</template>

<script>
import CardProduct from "./CardProduct.vue"
export default {
  name: "CardList",
  components: {
    CardProduct,
  },
  props: {
    productData: {
      type: Array,
      default: () => [],
    },
  },
}
</script>

<style lang="css" scoped>
.list {
  display: grid;
  grid-template-columns: repeat(3, 1fr);
}
</style>
