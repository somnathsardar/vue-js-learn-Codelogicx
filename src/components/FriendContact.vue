<template>
  <li>
    <h3>{{ name }}</h3>
    <button v-on:click="toggleSection()">Show details</button>
    <ul v-if="showDetails">
      <li><strong>Phone: </strong>{{ phone }}</li>
      <li><strong>Email: </strong>{{ email }}</li>
    </ul>
  </li>
</template>

<script>
export default {
  props: ["name", "phone", "email"],
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