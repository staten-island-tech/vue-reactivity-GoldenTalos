<template>
  <div class="card">
    <img v-bind:src="images" :alt="wname" />
    <h1 class="card-title">{{ wname }}</h1>
    <div class="card-info">
      <h2 class="price">${{ wprice }}</h2>
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
