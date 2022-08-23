<script>
import axios from "axios"
export default {
  data: function() {
    return {
      message: "Contact List",
      text: "Add a contact",
      contacts: [],
      newContact: {}
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
    },
    createContact: function() {
      console.log("creating new contact")
      axios.post("contacts", this.newContact).then(response =>{
        console.log(response.data);
      })
    },
    showContact: function() {
      console.log("Showing contact info")
    }
  }
};
</script>

<template>
  <div class="home">
    <h1>{{ message }}</h1>
    <hr />
    <!-- Add a new Contact -->
    <h3>{{ text }}</h3>
    <p><b>First Name:</b><input type="text" v-model="newContact.first_name"/></p>
    <p><b>Last Name:</b><input type="text" v-model="newContact.last_name"/></p>
    <p><b>Email:</b><input type="text" v-model="newContact.email"/></p>
    <p><b>Phone:</b><input type="text" v-model="newContact.phone_number"/></p>
    <p><b>Image:</b><input type="text" v-model="newContact.image"/></p>
    <button v-on:click="createContact">Add new contact</button>
    <hr />
    <!-- Display Contacts -->
    <div v-for="contact in contacts">
    <p>{{ contact.first_name }}
    {{ contact.last_name }}</p>
    <img :src="contact.image">
    <button v-on:click="showContact()">More Info</button>
    <br>
    <hr />
    </div>
  </div>
</template>

<style></style>