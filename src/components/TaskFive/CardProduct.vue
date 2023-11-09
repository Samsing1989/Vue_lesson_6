<template>
  <div class="body">
    <div class="item">
      <a :href="cardProduct.link" class="link">
        <div class="image"><img :src="cardProduct.imgSrc" /></div>
        <div class="title">{{ cardProduct.title }}</div>
        <div class="price">{{ cardProduct.price }} ₴</div>
      </a>
    </div>
  </div>
</template>

<script>
export default {
  name: "CardProduct",

  props: {
    cardProduct: {
      type: Object,
      default: () => ({}),
    },
  },
}
</script>

<style lang="css" scoped>
a {
  text-decoration: none;
  color: inherit;
}

.body {
  border: 2px solid #000;
  padding: 20px;
  text-align: center;
  width: 300px;
}
.item {
}
.link {
}
.image {
  margin-bottom: 10px;
}
.image img {
  max-width: 300px;
}
.title {
  font-size: 20px;
  color: blue;
  margin-bottom: 10px;
}
.price {
  color: red;
  font-size: 36px;
}
</style>
