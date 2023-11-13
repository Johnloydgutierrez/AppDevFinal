<template>
    <nav class="navbar navbar-dark bg-dark fixed-top">
  <div class="container-fluid">
    <a class="navbar-brand" href="">NWOW E-Bike</a>
    
    <button class="navbar-toggler" type="button" data-bs-toggle="offcanvas" data-bs-target="#offcanvasDarkNavbar" aria-controls="offcanvasDarkNavbar" aria-label="Toggle navigation">
      <span class="navbar-toggler-icon"></span>
    </button>
    <div class="offcanvas offcanvas-end text-bg-dark" tabindex="-1" id="offcanvasDarkNavbar" aria-labelledby="offcanvasDarkNavbarLabel">
      <div class="offcanvas-header">
        <h5 class="offcanvas-title" id="offcanvasDarkNavbarLabel">NWOW</h5>
        <button type="button" class="btn-close btn-close-white" data-bs-dismiss="offcanvas" aria-label="Close"></button>
      </div>
      <div class="offcanvas-body">
        <div class="input-group mb-3">
          <input type="text" class="form-control" placeholder="Search..." aria-label="Search" aria-describedby="search-button">
          <button class="btn btn-outline-secondary" type="button" id="search-button">Search</button>
        </div>
        <ul class="navbar-nav justify-content-end flex-grow-1 pe-3">
          <li class="nav-item">
            <li class="nav-item"><a class="nav-link" href="/Login">Login</a></li>
          </li>
          <li class="nav-item">
          </li>
        </ul>
      </div>
    </div>
  </div>
</nav>
                               
                                <li class="nav-item"><a class="nav-link" href="/Login">Login</a></li>

                               
                                
                            
                <section class="h-100 bg-dark">
  <div class="container py-5 h-100">
    <div class="row d-flex justify-content-center align-items-center h-100">
      <div class="col">
        <div class="card card-registration my-4">
          <div class="row g-0">
            <div class="col-xl-6 d-none d-xl-block">
              <div class="container">
    <img :src="require('@/assets/asset/css/logo.png')" alt="Centered Logo" class="centered-image" id="responsive-image">
</div>

                
            </div>
            <div class="col-xl-6">
              <div class="card-body p-md-5 text-black">
                <h3 class="mb-5 text-uppercase"> Registration Form</h3>

                <div class="row d-flex justify-content-center">
                  <div class="col-10 mb-2">
                    <div class="form-outline">
                      <input type="email" id="email" class="form-control form-control-lg" placeholder="name@example.com" required/>
                      <label class="form-label" for="email">Email</label>
                    </div>
                  </div>
                </div> 

                <div class="row d-flex justify-content-center">
                  <div class="col-10 mb-2">
                    <div class="form-outline">
                      <input type="text" id="username" class="form-control form-control-lg" required/>
                      <label class="form-label" for="username">Username</label>
                    </div>
                  </div>
                </div> 

                <div class="row d-flex justify-content-center">
                  <div class="col-10 mb-2">
                    <div class="form-outline">
                      <input type="password" id="password" class="form-control form-control-lg" required/>
                      <label class="form-label" for="password">Password</label>
                    </div>
                  </div>
                </div>

                <div class="row d-flex justify-content-center">
                  <div class="col-10 mb-2">
                    <div class="form-outline">
                      <input type="password" id="repassword" class="form-control form-control-lg" required/>
                      <label class="form-label" for="repassword">Re-type Password</label>
                    </div>
                  </div>
                </div>

                <div class="d-flex justify-content-end pt-3">
                  
                  <router-link to="/Login">
                    <button type="button"  class="btn btn-danger btn-lg ms-2" >Cancel</button>
                    </router-link>
                  <button type="button" class="btn btn-primary btn-lg ms-2">Submit form</button>
                </div>

              </div>
            </div>
          </div>
        </div>
      </div>
    </div>
  </div>
</section>
</template>
<style>
@import'../assets/asset/css/signup.css';
@import'../assets/asset/css/nfront.css';
.container {
 position: relative;
 width: 100%;
 height: 100%;
}

.centered-image {
 position: absolute;
 top: 50%;
 left: 50%;
 transform: translate(-50%, -50%) ;
 width: 50%; /* You can adjust this to fit your design */
 height: auto;
 z-index: 1; /* Make sure the image is above any other elements */
 pointer-events: none; /* Allows clicking through the image */
}


</style>
