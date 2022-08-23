<script>
import axios from "axios"
export default {
  data: function() {
    return {
      message: "Welcome to Vue.js!",
      text: "this is some text",
      contacts: []
    };
  },
  created: function() {},
  methods: {
    indexContacts: function() {
      axios.get("/contacts").then(response => {
        console.log(response.data);
        this.contacts = response.data
      })
    }
  }
};
</script>

<template>
  <div class="home">
    <h1>{{ message }}</h1>
    <h3>{{ text }}</h3>
    <p>{{ contacts }}</p>
    <button v-on:click="indexContacts">View Contacts</button>
  </div>
</template>

<style></style>