<template>
  <div class="card">
    <img v-bind:src="image" />
    <h1 class="card-title">{{ name }}</h1>
    <div class="card-info">
      <h3 class="price">${{ price }}</h3>
      <button @click="updateCharacter(index)">
        {{ name }}
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
