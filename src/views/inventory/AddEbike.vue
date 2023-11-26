<template>
    <div>
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
      <br>
      <br>
      <br>
  
      <div class="container mt-5">
        <h2 class="text-center mb-4">E-Bike List</h2>
  
        <!-- Add a button to toggle the form -->
        <button class="btn btn-primary" @click="toggleForm">Add E-Bike</button>
  
        <!-- Display the form when 'showForm' is true -->
        <div v-if="showForm" class="mt-4">
          <h3>{{ isEditing ? 'Edit E-Bike' : 'Add E-Bike' }}</h3>
          <form @submit.prevent="submitForm">
            <div class="mb-3">
              <label for="model" class="form-label">Model</label>
              <input type="text" class="form-control" id="model" v-model="formData.model" required />
            </div>
            <div class="mb-3">
              <label for="price" class="form-label">Price</label>
              <input type="text" class="form-control" id="price" v-model="formData.price" required />
            </div>
            <div class="mb-3">
              <label for="range" class="form-label">Range</label>
              <input type="text" class="form-control" id="range" v-model="formData.range" required />
            </div>
            <div class="mb-3">
              <label for="motorPower" class="form-label">Motor Power</label>
              <input type="text" class="form-control" id="motorPower" v-model="formData.motorPower" required />
            </div>
            <div class="mb-3">
              <label for="imageSrc" class="form-label">Image URL</label>
              <input type="text" class="form-control" id="imageSrc" v-model="formData.imageSrc" />
            </div>
            <div class="mb-3">
              <label for="category" class="form-label">Category</label>
              <select class="form-select" id="category" v-model="formData.category">
                <option value="Category A">Category A</option>
                <option value="Category B">Category B</option>
                <option value="Category C">Category C</option>
              </select>
            </div>
            <button type="submit" class="btn btn-success">Save</button>
          </form>
        </div>
        <div>
      <!-- ... (previous template code) ... -->
  
      <div class="row">
        <div class="col-md-4" v-for="(category, categoryIndex) in categories" :key="categoryIndex">
          <h2>{{ category.name }}</h2>
          <table class="table table-striped table-bordered mx-auto"> <!-- Center the table -->
            <thead class="thead-dark">
              <tr>
                <th>Model</th>
                <th>Price</th>
                <th>Range</th>
                <th>Motor Power</th>
                <th>Image</th>
                <th>Action</th>
              </tr>
            </thead>
            <tbody>
              <tr v-for="(ebike, index) in ebikes" :key="index">
                <template v-if="ebike.category === category.name">
                  <td>{{ ebike.model }}</td>
                  <td>{{ ebike.price }}</td>
                  <td>{{ ebike.range }}</td>
                  <td>{{ ebike.motorPower }}</td>
                  <td>{{ ebike.image }}</td>
                  <td>
                    <button class="btn btn-secondary" @click="editEbike(index)">Edit</button>
                    &nbsp;
                    <button class="btn btn-danger" @click="deleteEbike(index)">Delete</button>
                  </td>
                </template>
              </tr>
            </tbody>
          </table>
        </div>
      </div>
    </div>
      </div>
    </div>
  </template>
  
  <script>
  export default {
    data() {
      return {
        categories: [
          { name: '2 Wheels' },
          { name: '3 Wheels' },
          { name: '4 Wheels' },
        ],
        ebikes: [
          { model: 'E-Bike Model 1', price: '$1000', range: '50 miles', motorPower: '250W', imageSrc: 'path/to/your/image1.jpg', category: 'Category A' },
          { model: 'E-Bike Model 2', price: '$1200', range: '60 miles', motorPower: '350W', imageSrc: 'path/to/your/image2.jpg', category: 'Category B' },
          { model: 'E-Bike Model 3', price: '$900', range: '40 miles', motorPower: '200W', imageSrc: 'path/to/your/image3.jpg', category: 'Category A' },
          // Add more E-Bike data here with categories
        ],
        showForm: false,
        isEditing: false,
        formData: {
          model: '',
          price: '',
          range: '',
          motorPower: '',
          imageSrc: '',
          category: 'Category A', // Set a default category
        },
        editIndex: -1,
      };
    },
    methods: {
      toggleForm() {
        this.showForm = !this.showForm;
        this.isEditing = false;
        this.formData = {
          model: '',
          price: '',
          range: '',
          motorPower: '',
          imageSrc: '',
          category: 'Category A', // Reset the category when toggling the form
        };
      },
      submitForm() {
        if (this.isEditing) {
          this.ebikes[this.editIndex] = { ...this.formData };
        } else {
          this.ebikes.push({ ...this.formData });
        }
        this.toggleForm();
      },
      editEbike(index) {
        this.showForm = true;
        this.isEditing = true;
        this.formData = { ...this.ebikes[index] };
        this.editIndex = index;
      },
      deleteEbike(index) {
        this.ebikes.splice(index, 1);
      },
    },
  };
  </script>
  
  <style scoped>
  /* Add your component-specific styles here */
  
  </style>