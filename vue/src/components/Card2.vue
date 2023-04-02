<template>
  <div class="card">
    <img v-bind:src="image" />
    <h1 class="card-title">{{ name2 }}</h1>
    <div class="card-info">
      <h3 class="price">${{ price2 }}</h3>
      <button @click="updateWeapon(index)">
        {{ name2 }}
      </button>
    </div>
  </div>
</template>

<script>
export default {
  name: "Card",
  props: {
    title: String,
    image: String,
    price: String,
  },
  data() {
    return {};
  },
};
</script>
