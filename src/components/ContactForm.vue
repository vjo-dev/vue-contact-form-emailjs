<script setup>
import emailjs from "emailjs-com";
import { ref, computed } from "vue";

const name = ref("");
const email = ref("");
const message = ref("");

// disable submit button is form is incomplete
const buttonStatus = computed(() => {
  return name.value == "" || email.value == "" || message.value == "";
});

// action to submit the form
function sendEmail() {
  try {
    console.log("form submitted.");
  } catch (err) {
    if (err instanceof ReferenceError) {
      alert("JSON Error: " + err.message);
    } else {
      throw err; // rethrow
    }
  }

  // Reset form field
  name.value = "";
  email.value = "";
  message.value = "";
}
</script>

<template>
  <div class="container">
    <form v-on:submit.prevent="sendEmail">
      <label>Name</label>
      <input type="text" v-model="name" name="name" placeholder="Your Name" />
      <label>Email</label>
      <input
        type="email"
        v-model="email"
        name="email"
        placeholder="Your Email"
      />
      <label>Message</label>
      <textarea
        name="message"
        v-model="message"
        cols="30"
        rows="5"
        placeholder="Message"
      >
      </textarea>
      <input
        class="test"
        :class="buttonStatus ? 'disable' : 'enable'"
        :disabled="buttonStatus"
        type="submit"
        value="Send"
      />
    </form>
  </div>
</template>

<style>
.container {
  display: block;
  margin: auto;
  text-align: center;
  border-radius: 5px;
  background-color: #f2f2f2;
  padding: 20px;
  width: 50%;
  border: solid 2px green;
}

label {
  float: left;
}

input[type="text"],
[type="email"],
textarea {
  width: 100%;
  padding: 12px;
  border: 1px solid #ccc;
  border-radius: 10px;
  box-sizing: border-box;
  margin-top: 6px;
  margin-bottom: 16px;
  resize: vertical;
}

input[type="submit"]:disabled {
  background-color: grey;
  pointer-events: none;
  &:hover {
    background-color: grey;
  }
}

input[type="submit"] {
  background-color: #35495e;
  color: white;
  padding: 12px 20px;
  border: none;
  border-radius: 4px;
  cursor: pointer;
  &:not(.disable):hover {
    background-color: #41b883;
  }
}
</style>
