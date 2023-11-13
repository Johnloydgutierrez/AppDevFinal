<template>
  <nav class="navbar navbar-expand-lg navbar-dark bg-dark">
    <div class="container">
      <router-link to="/Admin" class="navbar-brand bg-dark">
        <svg xmlns="http://www.w3.org/2000/svg" width="30" height="30" fill="currentColor" class="bi bi-arrow-left-square-fill" viewBox="0 0 20 19">
  <path d="M16 14a2 2 0 0 1-2 2H2a2 2 0 0 1-2-2V2a2 2 0 0 1 2-2h12a2 2 0 0 1 2 2v12zm-4.5-6.5H5.707l2.147-2.146a.5.5 0 1 0-.708-.708l-3 3a.5.5 0 0 0 0 .708l3 3a.5.5 0 0 0 .708-.708L5.707 8.5H11.5a.5.5 0 0 0 0-1z"/>
</svg>Back</router-link>
      <button class="navbar-toggler" type="button" data-bs-toggle="collapse" data-bs-target="#navbarNav" aria-controls="navbarNav" aria-expanded="false" aria-label="Toggle navigation">
        <span class="navbar-toggler-icon"></span>
      </button>
      <div class="collapse navbar-collapse" id="navbarNav">
        <ul class="navbar-nav ml-auto">
        </ul>
      </div>
    </div>
  </nav>
  <div class="floating-container">
      <div class="right-container">
        <insert @data-saved="getInfo" />
      </div>
      <div class="parts-container">
        <br>
        <h2>E-Bike Parts Inventory</h2>
        <table border="1" class="parts-table">
          <tr>
            <th>Name</th>
            <th>Description</th>
            <th>Brand</th>
            <th>Model</th>
            <th>Quantity</th>
            <th>Price</th>
            <th>Action</th>
          </tr>
          <tr v-for="info in info" :key="info.id">
            <td>{{ info.name }}</td>
            <td>{{ info.description }}</td>
            <td>{{ info.brand }}</td>
            <td>{{ info.model }}</td>
            <td>{{ info.quantity }}</td>
            <td>{{ info.price }}</td>
            <td><button @click="deleteRecord(info.id)">Delete</button></td>
          </tr>
        </table>
      </div>
    </div>
  
</template>

<script>
import insert from '@/components/insert.vue';
import axios from 'axios';

export default {
  components: {
    insert,
  },
  data() {
    return {
      info: [],
    };
  },
  created() {
    this.getInfo();
  },
  methods: {
    async deleteRecord(id) {
     await axios.post("del",{
      id: id,
     });
     
     console.log(id);
     this.getInfo();
    },
    async getInfo() {
      try {
        const inf = await axios.get('getData');
        this.info = inf.data;
      } catch (error) {
        console.error('Error fetching data:', error);
      }
    },
  },
};
</script>
<style>
.floating-container  {
  display: flex;
  justify-content: space-between;
  width: 80%;
  margin: 20px auto;
  background-color: darkcyan;
  
}

.right-container {
  max-width: 500px;
}

.parts-container , h2{
  flex-grow: 1;
  padding-left: 20px;
  text-align: center;
}

.parts-table {
  width: 97%;
  border-collapse: collapse;
  margin-top: 20px;
}

.parts-table th,
.parts-table td {
  border: 1px solid #000000;
  padding: 20px;
  text-align: center;
  font-family: Impact, Haettenschweiler, 'Arial Narrow Bold', sans-serif;
  font-weight: 500;

}

.parts-table th {
  background-color: #f2f2f2;
}

.parts-table tr:nth-child(even) {
  background-color: #ffffff;
}

.right-container h2 {
  margin-bottom: 15px;
}

/* Added styling for the delete button */
.parts-table button {
  background-color: #3498db;
  color: #ffffff;
  border: none;
  padding: 8px 16px;
  cursor: pointer;
  border-radius: 4px;
}

.parts-table button:hover {
  background-color: #2980b9;
}

</style>

