<template>
  <div>
    <h2>{{ title }}:</h2>

    <div class="checkbox">
      <label class="label" v-for="(itemBrend, index) in listBrand" :key="index">
        <input
          :value="itemBrend"
          class="input"
          type="checkbox"
          v-model="checkbox"
        />
        {{ itemBrend }}</label
      >
    </div>
  </div>
</template>

<script>
export default {
  name: "CheckboxBrand",
  props: {
    listBrand: {
      type: Object,
      default: () => ({}),
    },
    title: {
      type: String,
    },
    modelTitle: {
      type: String,
    },

    modelValue: {
      type: Array,
      default: () => [],
    },
  },
  computed: {
    checkbox: {
      get() {
        return this.modelValue
      },
      set(val) {
        this.$emit("update:modelValue", val)
      },
    },
  },
}
</script>

<style lang="css" scoped>
.checkbox {
  display: flex;
  flex-direction: column;
  gap: 10px;
  font-size: 20px;
}
</style>
