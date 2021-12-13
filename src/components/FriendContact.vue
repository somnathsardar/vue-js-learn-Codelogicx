<template>
  <li>
    <h3>{{ friend.name }}</h3>
    <button v-on:click="toggleSection()">Show details</button>
    <ul v-if="showDetails">
      <li><strong>Phone: </strong>{{ friend.phone }}</li>
      <li><strong>Email: </strong>{{ friend.email }}</li>
    </ul>
  </li>
</template>

<script>
export default {
  props: ["friend"],
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