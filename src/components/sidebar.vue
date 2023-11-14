<template>
    <ul class="navbar-nav bg-green sidebar sidebar-dark accordion" id="accordionSidebar">

<!-- Sidebar - Brand -->
<a class="sidebar-brand d-flex align-items-center justify-content-center" href="/">
  <div class="sidebar-brand-icon rotate-n-15">
      <i class="fas fa-laugh-wink"></i>
  </div>
  <div class="sidebar-brand-text mx-3">NWOW E-BIKE <sup>Camilmil</sup></div>
</a>

<!-- Divider -->
<hr class="sidebar-divider my-0">

<!-- Nav Item - Dashboard -->
<li class="nav-item active">

  <a class="nav-link" href="/Admin">
      <i class="fas fa-fw fa-tachometer-alt"></i>
      <span>Admin Dashboard</span></a>

    

</li>

<!-- Divider -->
<hr class="sidebar-divider">

<!-- Heading -->
<div class="sidebar-heading">
  Inventory management
</div>

<!-- Nav Item - Pages Collapse Menu -->
<li class="nav-item">

  <a class="nav-link collapsed" href="#" data-toggle="collapse" data-target="#collapseTwo"
      aria-expanded="true" aria-controls="collapseTwo">
      <i class="fas fa-fw fa-cog"></i>
      <span>Inventory</span>
  </a>
  <div id="collapseTwo" class="collapse" aria-labelledby="headingTwo" data-parent="#accordionSidebar">
      <div class="bg-white py-2 collapse-inner rounded">
          <h6 class="collapse-header">List of Our Products</h6>
          <a class="collapse-item" href="/AddEbike">E-Bike List</a>
          <a class="collapse-item" href="/AddAssignment">Staff Assignment Service</a>
          <a class="collapse-item" href="/AddParts">Ebike Parts Products</a>
      </div>
  </div>

    

</li>

<!-- Nav Item - Utilities Collapse Menu -->
<li class="nav-item">

    <a class="nav-link collapsed" href="#" data-toggle="collapse" data-target="#collapseUtilities"
        aria-expanded="true" aria-controls="collapseUtilities">
        <i class="fas fa-fw fa-wrench"></i>
        <span>Sales Management</span>
    </a>
    <div id="collapseUtilities" class="collapse" aria-labelledby="headingUtilities"
        data-parent="#accordionSidebar">
       
    </div>
  
  <div id="collapseUtilities" class="collapse" aria-labelledby="headingUtilities"
      data-parent="#accordionSidebar">
      <div class="bg-white py-2 collapse-inner rounded">
          <h6 class="collapse-header">Sales Management:</h6>
          <a class="collapse-item" href="Sales">Sales</a>
          
      </div>
  </div>


</li>

<!-- Divider -->
<hr class="sidebar-divider">

<!-- Heading -->
<div class="sidebar-heading">
  Addons
</div>

<!-- Nav Item - Pages Collapse Menu -->
<li class="nav-item">
  <a class="nav-link collapsed" href="#" data-toggle="collapse" data-target="#collapsePages"
      aria-expanded="true" aria-controls="collapsePages">
      <i class="fas fa-fw fa-folder"></i>
      <span>Pages</span>
  </a>
  <div id="collapsePages" class="collapse" aria-labelledby="headingPages" data-parent="#accordionSidebar">
      <div class="bg-white py-2 collapse-inner rounded">
          
      </div>
  </div>
</li>

<!-- Nav Item - Charts -->


<!-- Nav Item - Charts -->
<li class="nav-item">
    <a class="nav-link" href="/charts">
        <i class="fas fa-fw fa-chart-area"></i>
        <span>Charts</span></a>
</li>

<!-- Nav Item - Tables -->
<li class="nav-item">
  <a class="nav-link" href="tables.html">
      <i class="fas fa-fw fa-table"></i>
      <span>Tables</span></a>
    

</li>

<!-- Divider -->
<hr class="sidebar-divider d-none d-md-block">

<!-- Sidebar Toggler (Sidebar) -->
<div class="text-center d-none d-md-inline">
  <button class="rounded-circle border-0" id="sidebarToggle"></button>
</div>

<!-- Sidebar Message -->


</ul>
</template>
export default{
  name:'sidebar'
}