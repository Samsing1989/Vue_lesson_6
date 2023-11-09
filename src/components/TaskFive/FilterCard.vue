<template>
  <div class="fit">
    <checkbox-brand
      title="Магазини"
      :list-brand="shops"
      v-model="checkedShop"
    />

    <checkbox-brand
      title="Бренди"
      :list-brand="brands"
      v-model="checkedBrand"
    />
  </div>
</template>

<script>
import CheckboxBrand from "./CheckboxBrand.vue"
export default {
  name: "FilterCard",
  components: {
    CheckboxBrand,
  },
  data() {
    return {
      shops: null,
      brands: null,
      checkedShop: [],
      checkedBrand: [],
    }
  },
  props: {
    notebooksData: {
      type: Array,
      default: () => [],
    },
  },
  watch: {
    checkedShop(value) {
      this.$emit("clickShop", value)
    },
    checkedBrand(value) {
      this.$emit("clickBrand", value)
    },
  },
  methods: {
    shopSort() {
      let set = new Set()
      this.notebooksData.forEach((element) => {
        set.add(element.shop)
      })
      this.shops = set
    },
    brandSort() {
      let set = new Set()
      this.notebooksData.forEach((element) => {
        set.add(element.brand)
      })
      this.brands = set
    },
  },
  created() {
    this.shopSort()
    this.brandSort()
  },
}
</script>

<style lang="css" scoped>
.fit {
  display: flex;
  flex-direction: column;
  align-items: center;
}
</style>
