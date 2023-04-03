<template>
  <div class="card">
    <img v-bind:src="images" />
    <h1 class="card-title">{{ wname }}</h1>
    <div class="card-info">
      <h3 class="price">${{ wprice }}</h3>
      <button @click="$emit('updateWeapon')">Add</button>
    </div>
  </div>
</template>

<script>
export default {
  name: "Card",
  props: {
    wname: String,
    images: String,
    wprice: Number,
  },
  data() {
    return {};
  },
};
</script>

<style>
img {
  width: 16rem;
  height: 23rem;
  object-fit: cover;
  border: solid black 3px;
}
</style>
