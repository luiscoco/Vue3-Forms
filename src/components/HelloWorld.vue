<template>
  <form @submit.prevent="login">
    <label for="username">Username:</label>
    <input type="text" id="username" v-model="username" />

    <label for="password">Password:</label>
    <input type="password" id="password" v-model="password" />

    <button type="submit">Login</button>
  </form>
</template>

<script lang="ts" setup>
import { ref } from "vue";

const username = ref("");
const password = ref("");

const login = () => {
  // Perform login logic here
  console.log("Username:", username.value);
  console.log("Password:", password.value);

  // Reset form fields
  username.value = "";
  password.value = "";
};
</script>
