<template>
  <section>
    <header><h1>My Friends</h1></header>
    <add-friend
      v-on:add-frind="addNewFriend"
      v-bind:addButtonText="addButtonText"
    ></add-friend>
    <ul v-if="friends.length">
      <friend-contact
        v-for="friend in friends"
        v-bind:key="friend.id"
        v-bind:friend="friend"
        v-on:toggle-favorite="toggleFavorite"
      ></friend-contact>
    </ul>
    <ul v-else>
      <li>You have no friens yet. Add new friend.</li>
    </ul>
  </section>
</template>

<script>
export default {
  data: function () {
    return {
      addButtonText: "Add new",
      friends: [],
    };
  },
  methods: {
    addNewFriend(friendData) {
      let tempData = {
        ...friendData,
        id: Date.now(),
      };
      this.addButtonText = "Adding...";
      setTimeout(() => {
        this.friends.unshift(tempData);
        this.addButtonText = "Added.";
        setTimeout(() => {
          this.addButtonText = "Add new";
        }, 1000);
      }, 2000);
    },
    toggleFavorite(friendId) {
      var myFriend = this.friends.find((f) => f.id === friendId);
      myFriend.isFavorite = !myFriend.isFavorite;
    },
  },
};
</script>

<style>
* {
  box-sizing: border-box;
}

html {
  font-family: "Jost", sans-serif;
}

body {
  margin: 0;
}

header {
  box-shadow: 0 2px 8px rgba(0, 0, 0, 0.26);
  margin: 3rem auto;
  border-radius: 10px;
  padding: 1rem;
  background-color: #58004d;
  color: white;
  text-align: center;
  width: 90%;
  max-width: 40rem;
}

#app ul {
  margin: 0;
  padding: 0;
  list-style: none;
}

#app li, 
#app form {
  box-shadow: 0 2px 8px rgba(0, 0, 0, 0.26);
  margin: 1rem auto;
  border-radius: 10px;
  padding: 1rem;
  text-align: center;
  width: 90%;
  max-width: 40rem;
}

#app h2 {
  font-size: 2rem;
  border-bottom: 4px solid #ccc;
  color: #58004d;
  margin: 0 0 1rem 0;
}

#app button {
  font: inherit;
  cursor: pointer;
  border: 1px solid #ff0077;
  background-color: #ff0077;
  color: white;
  padding: 0.05rem 1rem;
  box-shadow: 1px 1px 2px rgba(0, 0, 0, 0.26);
}

#app button:hover,
#app button:active {
  background-color: #ec3169;
  border-color: #ec3169;
  box-shadow: 1px 1px 4px rgba(0, 0, 0, 0.26);
}
</style>