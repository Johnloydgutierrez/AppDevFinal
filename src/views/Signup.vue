<template>
    <div class="container-fluid h-100 d-flex align-items-center justify-content-center">
      <v-sheet width="300" class="mx-auto floating-container">
        <img src="https://prof562e926-pic5.ysjianzhan.cn/upload/3002.png" alt="Logo" class="logo-image mb-4">
        <v-form fast-fail @submit.prevent="register">
          <div v-if="message === 'error'" class="error-message">Invalid response</div>
  
          <v-text-field v-model="username" label="Username"></v-text-field>
          <v-text-field v-model="password" label="Password" type="password"></v-text-field>
          <v-text-field v-model="passwordConfirm" label="Password Confirm" type="password"></v-text-field>
  
          <div v-if="message === 'passwordMismatch'" class="error-message">Passwords do not match</div>
  
          <v-btn type="submit" block class="mt-3">Submit</v-btn>
          <router-link to="/" class="d-block mt-2">Login</router-link>
        </v-form>
      </v-sheet>
    </div>
  </template>
  
  <script>
  import router from '@/router';
  import axios from 'axios';
  
  export default {
    data() {
      return {
        username: '',
        password: '',
        passwordConfirm: '',
        message: [],
      };
    },
    methods: {
      async register() {
        if (this.password === this.passwordConfirm) {
          const data = await axios.post("register", {
            username: this.username,
            password: this.password,
          });
  
          this.message = data.data.msg;
  
          if (data.data.msg === 'okay') {
            alert("Registered successfully");
            router.push('/');
          }
        } else {
          this.message = "passwordMismatch";
        }
      },
    },
  };
  </script>
  
  <style scoped>
  .floating-container {
    background-color: #fff;
    box-shadow: 0 0 10px rgba(0, 0, 0, 0.1);
    padding: 20px;
    border-radius: 10px;
    text-align: center; /* Center the content */
  }
  
  .logo-image {
    max-width: 100%;
    height: auto;
    margin-bottom: 20px;
  }
  *{
    
    font-family: 'Franklin Gothic Medium', 'Arial Narrow', Arial, sans-serif;
    font-weight: 300;
  }
  
  .error-message {
    color: red;
    margin-top: 10px;
  }
  </style>
  