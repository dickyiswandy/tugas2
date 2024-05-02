<template>
  <div class="background">
    <img src="https://i.pinimg.com/736x/6c/8f/01/6c8f01be1d4d76d7ffcc781710816051.jpg" />
  </div>
  <div class="content">
    <h1>Change Password</h1>
    <div v-if="successMessage" style="color: green;">{{ successMessage }}</div>
    <div v-if="errorMessage" style="color: red;">{{ errorMessage }}</div>
    <form @submit.prevent="changePassword">
      <label for="email">Email:</label><br>
      <input type="password" id="currentPassword" v-model="currentPassword"><br>
      <label for="currentPassword">Current Password:</label><br>
      <input type="password" id="currentPassword" v-model="currentPassword"><br>
      <label for="newPassword">New Password:</label><br>
      <input type="password" id="newPassword" v-model="newPassword"><br>
      <label for="confirmPassword">Confirm New Password:</label><br>
      <input type="password" id="confirmPassword" v-model="confirmPassword"><br>
      <button type="submit">Change Password</button>
    </form>
  </div>
</template>

<script setup>
import { ref } from 'vue';

const currentPassword = ref('');
const newPassword = ref('');
const confirmPassword = ref('');
const successMessage = ref('');
const errorMessage = ref('');

function changePassword() {
  if (newPassword.value !== confirmPassword.value) {
    errorMessage.value = "New password and confirm password don't match.";
    return;
  }

  setTimeout(() => {
    if (currentPassword.value === 'currentPassword123') {
      successMessage.value = "Password changed successfully!";
      errorMessage.value = '';
      currentPassword.value = '';
      newPassword.value = '';
      confirmPassword.value = '';
    } else {
      errorMessage.value = "Incorrect current password.";
    }
  }, 1000);
}
</script>

<style>
body {
  font-family: Arial, sans-serif;
  margin: 0;
  padding: 0;
  display: flex;
  justify-content: center;
  align-items: center;
  height: 100vh;
}

.background {
  position: fixed;
  top: 0;
  left: 0;
  width: 100%;
  height: 100%;
  z-index: -1;
}

.background img {
  width: 100%;
  height: 100%;
  object-fit: cover;
  filter: brightness(0.8);
}

.content {
  border: 1px solid white;
  padding: 20px;
  width: 300px;
}

h1 {
  margin-bottom: 20px;
  text-align: center;
  color: #fff;
}

form {
  display: flex;
  flex-direction: column;
}

label {
  margin-bottom: 5px;
  color: #fff;
}

input {
  padding: 8px;
  margin-bottom: 10px;
  border-radius: 4px;
  border: 1px solid #ccc;
  background-color: transparent;
  color: white;
}

button {
  background-color: #007bff;
  color: #fff;
  border: none;
  border-radius: 4px;
  padding: 10px;
  cursor: pointer;
}

button:hover {
  background-color: #0056b3;
}

.message {
  margin-top: 10px;
  text-align: center;
  font-weight: bold;
}
</style>
