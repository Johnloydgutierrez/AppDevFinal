<template>
  
    <div class="sidebar  text-light p-4">
      
      
      <h3>Add Product</h3>
      <form @submit.prevent="sve">
        <div class="mb-3">
          <label for="productName" class="form-label">productName</label>
          <input type="text" class="form-control" placeholder="productName" v-model="productName" required>
        </div>
  
        <div class="mb-3">
          <label for="description" class="form-label">description</label>
          <input type="text" class="form-control" placeholder="description" v-model="description" required>
        </div>
  
        <div class="mb-3">
          <label for="category" class="form-label">category</label>
          <input type="text" class="form-control" placeholder="category" v-model="category" required>
        </div>
  
        <div class="mb-3">
          <label for="price" class="form-label">price</label>
          <input type="text" class="form-control" placeholder="price" v-model="price" required>
        </div>
        
  
        
  
        <button type="submit" class="btn btn-success">Save</button>
        
      </form>
    </div>
  </template>
  
  <script>
  import axios from 'axios';
  
  export default {
    data() {
      return {
        productName: '',
        description: '',
        category: '',
        price: '',
     
        
      };
    },
    methods: {
      async sve() {
        try {
          const ins = await axios.post('save-product', {
            productName: this.productName,
            description: this.description,
            category: this.category,
        price: this.price,
       
        
          });
        this.productName ='';
        this.description ='';
        this.category ='';
        this.price ='';
        
  
        this.$emit('data-saved');
            this.getInfo(id);
        console.log(productName,description,category,price,)
  
          
        } catch (error) {
          console.log(error);
          
        }
       
      },
     
    },
  };
  </script>
  
  <style scoped>
  .sidebar {
    background-color: rgb(3, 187, 166);
    border-radius: 15px;
    overflow: hidden;
    width: 300px;
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
  
  .btn {
    padding: 8px 16px;
    cursor: pointer;
  }
  </style>
  