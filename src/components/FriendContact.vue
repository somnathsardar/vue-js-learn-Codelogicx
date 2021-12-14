<template>
  <li>
    <h3>{{ friend.name }} {{ friend.isFavorite ? "(Favorite)" : "" }}</h3>
    <button v-on:click="toggleSection()">Show details</button>
    <button @click="$emit('toggle-favorite', friend.id)">Toggle Favorite</button>
    <ul v-if="showDetails">
      <li><strong>Phone: </strong>{{ friend.phone }}</li>
      <li><strong>Email: </strong>{{ friend.email }}</li>
    </ul>
  </li>
</template>

<script>
export default {
  props: ["friend"],
  emits: ["toggle-favorite"],
  data: function() {
    return {
      showDetails: false,
    }
  },
  methods: {
    toggleSection() {
      this.showDetails = !this.showDetails;
    }
  }
}
</script>