<template>
  <nav class="navbar navbar-expand-lg pt-4 justify-content-center">
    <div class="container">
      <a href="/" class="navbar-brand d-flex w-50 me-auto">
        <img src="@/assets/logo.svg" alt="Foodnow Logo" class="img-fluid" />
      </a>
      <button class="navbar-toggler" type="button" data-bs-toggle="collapse" data-bs-target="#collapseNavbar">
        <span class="navbar-toggler-icon"></span>
      </button>
      <div class="navbar-collapse collapse w-100" id="collapseNavbar">
        <ul class="navbar-nav w-100 justify-content-center">
          <li v-for="(navItem, index) in nav" :key="index" class="nav-item">
            <a class="nav-link" href="#" id="navLink">{{ navItem.label }}</a>
          </li>
        </ul>
        <ul class="nav navbar-nav ms-auto w-100 justify-content-end align-items-center">
          <li class="nav-item me-3">
            <a class="nav-link" href="#" id="navLink">Login</a>
          </li>
          <li class="nav-item">
            <a class="nav-link" href="#" id="navLinkReg">Register</a>
          </li>
        </ul>
      </div>
    </div>
  </nav>
</template>

<script setup>
import { ref } from "vue";

const nav = ref([
  { label: "Home", path: "/" },
  { label: "Order", path: "/" },
  { label: "About", path: "/" },
  { label: "Blog", path: "/" },
  { label: "Contact Us", path: "/" },
]);
</script>

<style>
.img-fluid {
  width: 200px;
  margin-left: 0;
}

#navLink {
  color: white;
  font-size: 1.3rem;
  font-weight: 500;
  margin-right: 15px;
}

#navLink:hover {
  color: #e77e23;
}

#navLinkReg {
  color: white;
  font-size: 1.3rem;
  font-weight: 500;
  margin-right: 15px;
  background-color: #e77e23;
  width: 100px;
  height: 40px;
  padding-top: 9px;
  text-align: center;
  border-radius: 50px;
}

#navLinkReg:hover {
  background-color: #b4631b;
}
</style>
