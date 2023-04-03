<template>
  <div class="card">
    <img v-bind:src="image" :alt="name" />
    <h1 class="card-title">{{ name }}</h1>
    <div class="card-info">
      <h2 class="price">${{ price }}</h2>
      <button @click="$emit('updateCharacter')">Add</button>
    </div>
  </div>
</template>

<script>
export default {
  name: "Card",
  props: {
    name: String,
    image: String,
    price: Number,
  },
  data() {
    return {};
  },
};
</script>

<style>
.card {
  width: 12.7vw;
  height: 34rem;
  display: flex;
  flex-direction: column;
}
img {
  height: 29rem;
  width: 6rem;
  object-fit: cover;
  display: block;
}
.price {
  margin-top: 0px;
}
</style>
