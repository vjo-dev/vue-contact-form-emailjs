<script setup>
import emailjs from "emailjs-com";
import { ref } from "vue";

// fields
const namehjkl = ref("");
const emailhjkl = ref("");
const messagehjkl = ref("");
const isEmailInvalid = ref(false);
// otherunusedfield
const name = ref("Steve");
const email = ref("");
const message = ref("");

// function to reset field error
function resetInvalid() {
  if (isEmailInvalid.value) {
    isEmailInvalid.value = !isEmailInvalid.value;
  }
}

// action to submit the form
function sendEmail() {
  // prevent with otherunusedfield
  if (name.value != "Steve" || email.value != "" || message.value != "") {
    console.log("bot detected");
    return;
  }

  // email string validation
  if (!/^[\w-\.]+@([\w-]+\.)+[\w-]{2,4}$/.test(emailhjkl.value)) {
    console.log("invalid email");
    isEmailInvalid.value = true;
    return;
  }

  // sent form
  try {
    console.log("form submitted.");
  } catch (err) {
    if (err instanceof ReferenceError) {
      alert("JSON Error: " + err.message);
    } else {
      throw err; // rethrow
    }
  }

  // Reset fields
  namehjkl.value = "";
  emailhjkl.value = "";
  messagehjkl.value = "";
  isEmailInvalid.value = false;

  // Reset otherunusedfield
  name.value = "Steve";
  email.value = "";
  message.value = "";
}
</script>

<template>
  <div class="container">
    <form v-on:submit.prevent="sendEmail">
      <!-- fields -->
      <label>Name</label>
      <input
        type="text"
        v-model="namehjkl"
        name="namehjkl"
        placeholder="Your Name"
        maxlength="100"
        required
      />
      <label>Email</label>
      <input
        :class="{ invalid: isEmailInvalid }"
        @click="resetInvalid"
        type="email"
        v-model="emailhjkl"
        name="emailhjkl"
        placeholder="Your Email"
        required
      />
      <label>Message</label>
      <textarea
        name="messagehjkl"
        v-model="messagehjkl"
        cols="30"
        rows="5"
        placeholder="Message"
        required
      >
      </textarea>
      <input type="submit" value="Send" />

      <!-- otherunusedfield -->
      <label class="fields">Name</label>
      <input
        class="fields"
        type="text"
        v-model="name"
        name="name"
        placeholder="Your Name"
        autocomplete="off"
        required
      />
      <label class="fields">Email</label>
      <input
        class="fields"
        type="email"
        v-model="email"
        name="email"
        placeholder="Your Email"
        autocomplete="off"
      />
      <label class="fields">Message</label>
      <textarea
        class="fields"
        name="message"
        v-model="message"
        cols="30"
        rows="5"
        placeholder="Message"
        autocomplete="off"
      >
      </textarea>
    </form>
  </div>
</template>

<style>
.fields {
  opacity: 0;
  position: absolute;
  top: 0;
  left: 0;
  height: 0;
  width: 0;
  z-index: -1;
}

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
  font-size: 1em;
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

.invalid {
  border: solid 4px red;
}
</style>
