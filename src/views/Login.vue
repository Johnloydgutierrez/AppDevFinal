<template>
  <div class="background-container">
    <!-- Your content goes here -->
    
      <!-- Your container content -->
    
  
  <div class="container">
  <div class="container-fluid d-flex align-items-center justify-content-center vh-100">
    <div class="v-container theme-container">
      <img src="https://prof562e926-pic5.ysjianzhan.cn/upload/3002.png" alt="Logo" class="logo-image mb-4">
      <v-sheet width="300" class="mx-auto">
        <v-form @submit.prevent="login">
          <div v-if="message === 'error'" class="error-message">Invalid response</div>

          <v-text-field v-model="username" label="Username" outlined :color="rayColor"></v-text-field>
          <v-text-field v-model="password" label="Password" type="password" outlined :color="rayColor"></v-text-field>

          <v-btn type="submit" block class="mt-3" color="orange">Login</v-btn>
          <router-link to="/signup" class="d-block mt-2">
  <v-btn color="pink" block>
    Don't have an account?
  </v-btn>
</router-link>

        </v-form>
      </v-sheet>
    </div>
  </div>
</div>
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
      message: '',
      rayColor: 'green',
    };
  },
  methods: {
    async login() {
      try {
        const { data } = await axios.post('login', {
          username: this.username,
          password: this.password,
        });

        this.message = data.msg;

        if (data.msg === 'okay') {
          sessionStorage.setItem('jwt', data.token);
          router.push('/Nhome');
        }
      } catch (error) {
        console.error('An error occurred during login:', error);
        this.message = 'error';
      }
    },
  },
};
</script>

<style scoped>
.logo-image {
  max-width: 100%;
  height: auto;
}

.theme-container {
  background-color: rgb(255, 255, 255); /* White background */
  padding: 20px;
  border-radius: 15px; /* Increased border radius for curved edges */
  box-shadow: 0 0 20px rgba(41, 33, 33, 0.2); /* Adjusted box shadow */
}

.error-message {
  color: red;
  margin-top: 10px;
}

/* Custom color for ray (outlined text field) */
.theme--light.v-text-field--outlined:not(.v-text-field--dense):not(.v-text-field--textarea) {
  border-color: rgb(45, 202, 45);
}

/* Adjusted color for the button */
.v-btn--contained.orange {
  color: #fff;
  background-color: orange;
}
.background-container {
  background-color: rgb(32, 139, 37); /* Blue background color, change to your preferred color */
  height: 100vh; /* Full height of the viewport, adjust as needed */
  display: flex;
  align-items: center;
  justify-content: center;
}

.container {
  /* Your container styles go here */
  padding: 20px;
  border-radius: 10px;
  /* Other styles */
}
</style>
