<template>
  <div class="sidebar bg-green text-light p-4">
    <h3>Add New Product</h3>
    <form @submit.prevent="save">
      <div class="mb-3">
        <label for="name" class="form-label">Name</label>
        <input type="text" class="form-control" placeholder="Name" v-model="name" required>
      </div>
      
      <div class="mb-3">
        <label for="Description" class="form-label">Description</label>
        <input type="text" class="form-control" placeholder="Description" v-model="description" required>
      </div>

            
      <div class="mb-3">
        <label for="Brand" class="form-label">Brand</label>
        <input type="text" class="form-control" placeholder="Brand" v-model="brand" required>
      </div>
      
            
      <div class="mb-3">
        <label for="Model" class="form-label">Model</label>
        <input type="text" class="form-control" placeholder="Model" v-model="model" required>
      </div>

            
      <div class="mb-3">
        <label for="Quantity" class="form-label">Quantity</label>
        <input type="text" class="form-control" placeholder="Quantity" v-model="quantity" required>
      </div>

      <div class="mb-3">
        <label for="image" class="form-label">Image</label>
        <input type="file" id="image" class="form-control" @change="handleImageChange" required>
      </div>

            
      <div class="mb-3">
        <label for="Price" class="form-label">Price</label>
        <input type="text" class="form-control" placeholder="Price" v-model="price" required>
      </div>

      <button type="submit" class="btn btn-danger">Save</button>
    </form>
  </div>
</template>

<script>
import axios from 'axios';

export default {
  data() {
    return {
      name: '',
      description: '',
      brand: '',
      model: '',
      quantity: '',
      image: null,
      price: '',
    };
  },
  methods: {
    handleImageChange(event) {
      this.image = event.target.files[0];
    },
    async save() {
      try {
        const formData = new FormData();
        formData.append('name', this.name);
        formData.append('description', this.description);
        formData.append('brand', this.brand);
        formData.append('model', this.model);
        formData.append('quantity', this.quantity);
        formData.append('image', this.image);
        formData.append('price', this.price);

        const response = await axios.post('save', formData, {
          headers: {
            'Content-Type': 'multipart/form-data',
          },
        });

        console.log(response.data);

        // ... handle other responses or actions as needed
      } catch (error) {
        console.error(error);
      }
    },
  },
};
</script>

  
  <style scoped>
  
  .sidebar {
    height: 100vh;
  }
  
  .sidebar h3 {
    margin-bottom: 20px;
  }
  
  .sidebar label {
    margin-bottom: 5px;
  }
  
  .sidebar input {
    margin-bottom: 15px;
  }
  
  .sidebar button {
    margin-top: 10px;
  }
  .sidebar-container {
  height: 0vh; /* 100% of the viewport height */
  display: flex;
  flex-direction: column;
}

.sidebar {
  height: 100%; /* Occupy full height of the container */
}
  
  </style>
  