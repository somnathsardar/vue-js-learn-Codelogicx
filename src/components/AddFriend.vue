<template>
  <form ref="friendForm">
    <div>
      <label for="name">Name</label>
      <input
        type="text"
        v-model="name"
        id="name"
        placeholder="Enter name"
        autocomplete="false"
      />
    </div>
    <div>
      <label for="email">Email</label>
      <input
        type="email"
        v-model="email"
        id="email"
        placeholder="Enter email"
        autocomplete="false"
      />
    </div>
    <div>
      <label for="phone">Phone</label>
      <input
        type="tel"
        v-model="phone"
        id="phone"
        placeholder="Enter phone"
        autocomplete="false"
      />
    </div>
    <div>
      <input type="checkbox" v-model="isFavorite" id="favorite" />
      <label for="favorite">Is favorite?</label>
    </div>
    <div>
      <button type="submit" @click.prevent="addFriend()">
        {{ addButtonText }}
      </button>
    </div>
  </form>
</template>

<script>
export default {
  emits: ["add-frind"],
  props: ["addButtonText"],
  // watch: {
  //   addButtonText(newValue) {
  //     if(newValue === "Add new") {
  //       console.log(this.$refs.friendForm)
  //     }
  //   }
  // },
  methods: {
    addFriend() {
      if (this.name || this.email || this.phone) {
        let sendItem = {
          name: this.name,
          email: this.email,
          phone: this.phone,
          isFavorite: this.isFavorite,
        };
        this.$emit("add-frind", sendItem);
      } else {
        alert("Please provide all the necessary field.");
      }
    },
  },
  data: function () {
    return {
      name: "",
      email: "",
      phone: null,
      isFavorite: false,
    };
  },
};
</script>

<style scoped>
/* form {
  width: 90%;
  margin: 3rem auto;
  max-width: 40rem;
  box-shadow: 0 2px 8px rgb(0 0 0 / 26%);
  padding: 8px;
}
form div {
  padding: 8px;
  display: flex;
  align-items: center;
}
form div label {
  margin-right: 8px;
} */

form div input {
  border: none;
  outline: none;
  border-bottom: 1px solid #b5b0b0;
}
#app input {
  font: inherit;
  padding: 0.15rem;
}
#app label {
  font-weight: bold;
  margin-right: 1rem;
  width: 7rem;
  display: inline-block;
}
#app form div {
  margin: 1rem 0;
}
</style>