<script>
export default {
  data: function() {
    return {
      message: "Welcome to Vue.js!",
      text: "this is some text"
    };
  },
  created: function() {},
  methods: {
    indexContacts: function() {}
  }
};
</script>

<template>
  <div class="home">
    <h1>{{ message }}</h1>
    <h3>{{ text }}</h3>
    <button v-on:click="indexContacts">View Contacts</button>
  </div>
</template>

<style></style>