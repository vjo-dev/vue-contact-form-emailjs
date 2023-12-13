<template>
  <div>
    <img src="./assets/logo.png" alt="vue-logo" />
    <ContactForm />
  </div>
</template>

<script>
import ContactForm from "./components/ContactForm.vue";

export default {
  name: "App",
  components: {
    ContactForm,
  },
};
</script>

<style>
*,
*::after,
*::before {
  box-sizing: border-box;
}

body {
  padding: 0;
  margin: 0;
  position: relative;
  height: auto;
  min-height: 100% !important;
  font-style: normal;
  font-size: calc(16px + 0.390625vw);
  font-family: "Segoe UI", -apple-system, BlinkMacSystemFont, "Roboto", "Oxygen",
    "Ubuntu", "Cantarell", "Fira Sans", "Droid Sans", "Helvetica Neue",
    sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
}

#app {
  background-color: lightgrey;
  height: 100vh;
  width: 100vw;
  display: flex;
  flex-direction: column;
  justify-content: space-evenly;
  text-align: center;
}
</style>
