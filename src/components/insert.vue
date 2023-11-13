<template>
    <div class="sidebar bg-green text-light p-4">
        <div>
    
  </div>
      <h3>Add New Product</h3>
      
      <form @submit.prevent="save">
        <div class="mb-3">
          <label for="name" class="form-label">Name</label>
          <input type="text" class="form-control" placeholder="Name" v-model="name">
        </div>
  
        <div class="mb-3">
          <label for="description" class="form-label">Description</label>
          <input type="text" class="form-control" placeholder="Description" v-model="description">
        </div>
  
        <div class="mb-3">
          <label for="brand" class="form-label">Brand</label>
          <input type="text" class="form-control" placeholder="Brand" v-model="brand">
        </div>
  
        <div class="mb-3">
          <label for="model" class="form-label">Model</label>
          <input type="text" class="form-control" placeholder="Model" v-model="model">
        </div>
  
        <div class="mb-3">
          <label for="quantity" class="form-label">Quantity</label>
          <input type="text" class="form-control" placeholder="Quantity" v-model="quantity">
        </div>
  
        <div class="mb-3">
          <label for="price" class="form-label">Price</label>
          <input type="text" class="form-control" placeholder="Price" v-model="price">
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
        price: '',
        
      };
    },
    methods: {
      async save() {
        try {
          const ins = await axios.post('save', {
            name: this.name,
            description: this.description,
            brand: this.brand,
            model: this.model,
            quantity: this.quantity,
            price: this.price,
           
          });
  
          this.name = '';
          this.description = '';
          this.brand = '';
          this.model = '';
          this.quantity = '';
          this.price = '';
          
  
          this.$emit('data-saved');
          this.getInfo(id);
  
          console.log(name, description, brand, model, quantity, price, );
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
  