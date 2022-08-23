<script>
import axios from "axios"
export default {
  data: function() {
    return {
      message: "Contact List",
      text: "These are your contacts",
      contacts: []
    };
  },
  created: function() {
    this.indexContacts()
  },
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
    <hr />
    <div v-for="contact in contacts">
    <p>{{ contact.first_name }}
    {{ contact.last_name }}</p>
    <p>{{ contact.email }}</p>
    <p>{{ contact.phone_number }}</p>
    <img :src="contact.image">
    <br>
    <hr />
    </div>
  </div>
</template>

<style></style>