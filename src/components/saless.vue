<template> 
  <div class="container-fluid bg-cyan">
    <div id="content">
      <div id="content">
  <div class="row">
<!-- Earnings (Monthly) Card Example -->
<div class="col-xl-3 col-md-6 mb-4">
  <div class="card border-left-primary shadow h-100 py-2">
      <div class="card-body">
          <div class="row no-gutters align-items-center">
              <div class="col mr-2">
                  <div class="text-xs font-weight-bold text-primary text-uppercase mb-1">
                      Paid</div>
                  <div class="h5 mb-0 font-weight-bold text-gray-800">1</div>
              </div>
              <div class="col-auto">
                  <i class="fas fa-calendar fa-2x text-gray-300"></i>
              </div>
          </div>
      </div>
  </div>
</div>
<!-- Earnings (Monthly) Card Example -->
<div class="col-xl-3 col-md-6 mb-4">
  <div class="card border-left-success shadow h-100 py-2">
      <div class="card-body">
          <div class="row no-gutters align-items-center">
              <div class="col mr-2">
                  <div class="text-xs font-weight-bold text-success text-uppercase mb-1">
                      Installment</div>
                  <div class="h5 mb-0 font-weight-bold text-gray-800">2</div>
              </div>
              <div class="col-auto">
                  <i class="fas fa-dollar-sign fa-2x text-gray-300"></i>
              </div>
          </div>
      </div>
  </div>
</div>
<!-- Earnings (Monthly) Card Example -->
<div class="col-xl-3 col-md-6 mb-4">
  <div class="card border-left-info shadow h-100 py-2">
      <div class="card-body">
          <div class="row no-gutters align-items-center">
              <div class="col mr-2">
                  <div class="text-xs font-weight-bold text-info text-uppercase mb-1">Unpaid
                  </div>
                  <div class="row no-gutters align-items-center">
                      <div class="col-auto">
                          <div class="h5 mb-0 mr-3 font-weight-bold text-gray-800">3</div>
                      </div>
                  </div>
              </div>
              <div class="col-auto">
                  <i class="fas fa-clipboard-list fa-2x text-gray-300"></i>
              </div>
          </div>
      </div>
  </div>
</div>
<!-- Pending Requests Card Example -->
<div class="col-xl-3 col-md-6 mb-4">
  <div class="card border-left-warning shadow h-100 py-2">
      <div class="card-body">
          <div class="row no-gutters align-items-center">
              <div class="col mr-2">
                  <div class="text-xs font-weight-bold text-warning text-uppercase mb-1">
                    Total</div>
                  <div class="h5 mb-0 font-weight-bold text-gray-800">6</div>
              </div>
              <div class="col-auto">
                  <i class="fas fa-comments fa-2x text-gray-300"></i>
              </div>
          </div>
      </div>
  </div>
</div>
</div>
<div class="row">
<!-- Area Chart -->
<div class="col-xl-8 col-lg-7">
  <div class="col-sm-12 col-xl-6">
                      <div class="bg-light text-center rounded p-4">
                          <div class="d-flex align-items-center justify-content-between mb-4">
                              <h6 class="mb-0">Worldwide Sales</h6>
                              <a href="">Show All</a>
                          </div>
                          <canvas id="worldwide-sales"></canvas>
                      </div>
                  </div>
</div>
<!-- Pie Chart -->
<div class="col-xl-4 col-lg-5">
  <div class="card shadow mb-4">
      <!-- Card Header - Dropdown -->
      <div
          class="card-header py-3 d-flex flex-row align-items-center justify-content-between">
          <h6 class="m-0 font-weight-bold text-primary">Revenue Sources</h6>
      </div>
      <!-- Card Body -->
      <div class="card-body">
          <div class="chart-pie pt-4 pb-2">
              <canvas id="myPieChart"></canvas>
          </div>
          <div class="mt-4 text-center small">
              <span class="mr-2">
                  <i class="fas fa-circle text-primary"></i> Direct
              </span>
              <span class="mr-2">
                  <i class="fas fa-circle text-success"></i> Social
              </span>
              <span class="mr-2">
                  <i class="fas fa-circle text-info"></i> Referral
              </span>
          </div>
      </div>
  </div>
</div>
</div>
</div>
<div class="container-fluid pt-4 px-4">
              <div class="bg-light text-start rounded p-4">
                  <div class="d-flex align-items-center mb-4">
                      <h6 class="col mr-2">Recent Sales</h6>
              
                      <div class="d-flex justify-content-center mr-2">
<a class="btn btn-primary" data-bs-toggle="offcanvas" href="#offcanvasExample" role="button" aria-controls="offcanvasExample">Create Ebike Invoice</a>
<div class="offcanvas offcanvas-end" id="offcanvasExample" aria-labelledby="offcanvasExampleLabel">
<div class="offcanvas-header">
  <h5 class="offcanvas-title" id="offcanvasExampleLabel">New Ebike Invoice</h5>
  <button type="button" class="btn-close" data-bs-dismiss="offcanvas" aria-label="Close"></button>
</div>
<div class="bg-blue offcanvas-body">
  <div class="text-light">
    <form>
      <div class="mb-3">
        <label for="date" class="form-label">Date</label>
        <input type="date" class="form-control" placeholder="Date" v-model="date" required>
      </div>

      <div class="mb-3">
        <label for="customer" class="form-label">Customer</label>
        <input type="text" class="form-control" placeholder="Customer" v-model="customer" required>
      </div>

      <div class="mb-3">
        <label for="category" class="form-label">Category</label>
        <select id="category" class="form-select" v-model="category" required>
<option value="Ebike">E-Bike</option></select>
      </div>

      <div class="mb-3">
        <label for="product" class="form-label">Product</label>
        <select id="productSelect" class="form-select"  v-model="product" @change="updateTotal">
<option value="" disabled selected>Select option</option>
<option v-for="elist in elist" :key="elist.id" :value="elist.id">{{ elist.model }} - ₱{{ elist.price }}</option> //elist
</select>
      </div>

      <div class="mb-3">
      <label for="quantityInput">Quantity:</label>
  <input type="number" id="quantityInput" class="form-control" v-model.number="quantity" @input="updateTotal" />
</div>

<div class="mb-3">
  <label for="totalAmount">Total Amount:</label>
  <p class="form-control" id="totalAmount">₱{{ totalAmount }}</p>
</div>

      <button type="submit" class="btn btn-danger">Invoice</button>
    </form>
  </div>
</div>
</div>
</div>

<div class="d-flex justify-content-center mr-2">
<a class="btn btn-primary" data-bs-toggle="offcanvas" href="#ebikeparts" role="button" aria-controls="ebikeparts">Create Ebike Parts Invoice</a>
<div class="offcanvas offcanvas-end" id="ebikeparts" aria-labelledby="ebikepartss">
<div class="offcanvas-header">
  <h5 class="offcanvas-title" id="ebikepartss">New Ebike Invoice</h5>
  <button type="button" class="btn-close" data-bs-dismiss="offcanvas" aria-label="Close"></button>
</div>
<div class="bg-blue offcanvas-body">
  <div class="text-light">
    <form>
      <div class="mb-3">
        <label for="date" class="form-label">Date</label>
        <input type="date" class="form-control" placeholder="Date" v-model="date" required>
      </div>

      <div class="mb-3">
        <label for="customer" class="form-label">Customer</label>
        <input type="text" class="form-control" placeholder="Customer" v-model="customer" required>
      </div>

      <div class="mb-3">
        <label for="category" class="form-label">Category</label>
        <select id="category" class="form-select" v-model="category" required>
<option value="Ebike">E-Bike Parts</option></select>
      </div>

      <div class="mb-3">
        <label for="parts" class="form-label">Product</label>
        <select id="partsSelect" class="form-select"  v-model="parts" @change="updateTotalp">
<option value="" disabled selected>Select option</option>
<option v-for="ebikeparts in ebikeparts" :key="ebikeparts.ID" :value="ebikeparts.ID">{{ ebikeparts.name }} - ₱{{ ebikeparts.price }}</option> //parts
</select>
      </div>

      <div class="mb-3">
      <label for="quantityInput">Quantity:</label>
  <input type="number" id="quantityInput" class="form-control" v-model.number="quantity" @input="updateTotalp" />
</div>

<div class="mb-3">
  <label for="totalAmountp">Total Amount:</label>
  <p class="form-control" id="totalAmountp">₱{{ totalAmountp }}</p>
</div>

      <button type="submit" class="btn btn-danger">Invoice</button>
    </form>
  </div>
</div>
</div>
</div>

                  </div>
                  <div class="table-responsive">
                      <table class="table text-start align-middle table-bordered table-hover mb-0">
                          <thead>
                              <tr class="text-dark">   
                                  <th scope="col">Date</th>
                                  <th scope="col">Customer</th>
                                  <th scope="col">Category</th>
                                  <th scope="col">Product</th>
                                  <th scope="col">Amount</th>
                                  <th scope="col">Action</th>
                              </tr>
                          </thead>
                          <tbody>
                          </tbody>
                      </table>
                  </div>
              </div>
          </div>
    </div>
  </div>
</template>

<script>
import axios from 'axios';
export default {
  
  data() {
    return {
      elist: [],
      ebikeparts: [],
      selectedProduct: null,
      selectedParts: null,
      quantity: 1,
      totalAmount: 0,
      totalAmountp: 0
    };
  },
  mounted() {
    this.fetchProducts();
    this.fetchParts();
  },
  methods: {
    fetchProducts() {

      axios.get('getEList')
        .then(response => {
          this.elist = response.data;
        })
        .catch(error => {
          console.error('Error fetching products:', error);
        });
    },
        fetchParts() {

      axios.get('getPartss')
        .then(response => {
          this.ebikeparts = response.data;
        })
        .catch(error => {
          console.error('Error fetching parts:', error);
        });
    },

    updateTotal() {
      if (this.product !== null) {
        const product = this.elist.find(elist => elist.id === this.product);
        this.totalAmount = product.price * this.quantity;
      } else {
        this.totalAmount = 0;
      }
    },

    updateTotalp() {
      if (this.parts !== null) {
        const parts = this.ebikeparts.find(ebikeparts => ebikeparts.ID === this.parts);
        this.totalAmountp = parts.price * this.quantity;
      } else {
        this.totalAmountp = 0;
      }
    }
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
