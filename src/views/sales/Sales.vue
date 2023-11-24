<template>
    
  <nav class="navbar navbar-expand-lg navbar-dark bg-dark">
  <div class="container">
    <router-link to="/Admin" class="navbar-brand bg-dark">
      <svg xmlns="http://www.w3.org/2000/svg" width="30" height="30" fill="currentColor" class="bi bi-arrow-left-square-fill" viewBox="0 0 20 19">
<path d="M16 14a2 2 0 0 1-2 2H2a2 2 0 0 1-2-2V2a2 2 0 0 1 2-2h12a2 2 0 0 1 2 2v12zm-4.5-6.5H5.707l2.147-2.146a.5.5 0 1 0-.708-.708l-3 3a.5.5 0 0 0 0 .708l3 3a.5.5 0 0 0 .708-.708L5.707 8.5H11.5a.5.5 0 0 0 0-1z"/>
</svg>Back</router-link>  
    <div class="collapse navbar-collapse" id="navbarNav">   
    </div>
  </div>
</nav>
<div class="right-container">
        <saless/>
      </div>

</template>

<script>
import saless from '@/components/saless.vue';

export default {
  components: {
    saless,
  }
};
</script>

<style scoped>
.container-fluid {
  background-color: rgb(0, 255, 221); /* Set your desired green color code */
  padding: 20px; /* Adjust padding as needed */
}

/* Add any additional styles for the container */
</style>
