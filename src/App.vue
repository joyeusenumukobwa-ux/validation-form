<script setup>
import { ref } from 'vue'

const username = ref('')
const email = ref('')
const password = ref('')

const error = ref('')

function validateForm() {
  error.value = ''

  if (username.value === '') {
    error.value = 'Username is required'
    return
  }

  if (email.value === '') {
    error.value = 'Email is required'
    return
  }

  if (!email.value.includes('@')) {
    error.value = 'Please enter a valid email'
    return
  }

  if (password.value === '') {
    error.value = 'Password is required'
    return
  }

  alert('Login successful!')
}
</script>

<template>
  <div class="login-container">
    <div class="login-box">
      <h1>Login Form</h1>

      <form @submit.prevent="validateForm">

        <label for="username">Username:</label>
        <input
          type="text"
          id="username"
          placeholder="Enter username"
          v-model="username"
        >

        <label for="email">Email:</label>
        <input
          type="email"
          id="email"
          placeholder="Enter email"
          v-model="email"
        >

        <label for="password">Password:</label>
        <input
          type="password"
          id="password"
          placeholder="Enter password"
          v-model="password"
        >

        <p v-if="error" class="error">{{ error }}</p>

        <button type="submit">Login</button>

        <p>
          Don't have an account?
          <a href="#">Register</a>
        </p>

      </form>
    </div>
  </div>
</template>