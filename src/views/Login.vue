<template>
  <div class="container d-flex align-items-center justify-content-center h-100">
    <div class="v-container theme-container">
      <img src="https://prof562e926-pic5.ysjianzhan.cn/upload/3002.png" alt="Logo" class="logo-image mb-4">
      <v-sheet width="300" class="mx-auto">
        <v-form @submit.prevent="login">
          <div v-if="message === 'error'" class="error-message">Invalid response</div>

          <v-text-field v-model="username" label="Username"></v-text-field>
          <v-text-field v-model="password" label="Password" type="password"></v-text-field>

          <v-btn type="submit" block class="mt-3">Submit</v-btn>
          <router-link to="/signup" class="d-block mt-2">Register</router-link>
        </v-form>
      </v-sheet>
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
  background-color: rgb(255, 255, 255); /* light blue background */
  padding: 20px;
  border-radius: 10px;
  box-shadow: 0 0 10px rgba(41, 33, 33, 0.1);
}

.error-message {
  color: red;
  margin-top: 10px;
}
</style>
