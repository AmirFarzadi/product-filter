<template>
  <div class="container mb-5">
    <h3 class="text-center mt-3">محصولات ما</h3>
    <nav class="navbar navbar-expand-lg justify-content-center p-4">
      <div id="navbarNav">
        <ul class="navbar-nav">
          <li class="nav-item" @click="clickHandler('همه')">
            <a class="nav-link" href="#">همه</a>
          </li>
          <li class="nav-item" @click="clickHandler('موبایل')">
            <a class="nav-link" href="#">موبایل</a>
          </li>
          <li class="nav-item" @click="clickHandler('لپ تاپ')">
            <a class="nav-link" href="#">لپ تاپ</a>
          </li>
          <li class="nav-item" @click="clickHandler('هدفون')">
            <a class="nav-link" href="#">هدفون</a>
          </li>
        </ul>
      </div>
    </nav>
    <div id="productTemplate">
      <div class="card p-2" v-for="data in database" :key="data.id">
        <img :src="data.img" class="card-img-top" alt="..." />

        <div class="card-body">
          <h5 class="card-title">{{ data.title }}</h5>
          <p class="card-text">{{ data.description }}</p>
        </div>
        <div
          class="card-footer d-flex flex-row align-items-center justify-content-between"
        >
          <a href="#" class="btn btn-outline-primary">
            <i class="bi bi-cart3"></i>
          </a>
          <h6 id="price" class="m-0">{{ data.price }}T</h6>
        </div>
      </div>
    </div>
  </div>
</template>

<script setup>
import { ref } from "vue";
import products from "./data";
const database = ref(products);
const categorySelectedProducts = ref(null);
function clickHandler(id) {
  if (id !== "همه") {
    categorySelectedProducts.value = products.filter((element) => {
      return id == element.category;
    });
    database.value = categorySelectedProducts.value;
  } else {
    database.value = products;
  }
}
</script>

<style>
body {
  background-color: #f1f2f6 !important;
}
#productTemplate {
  display: grid;
  grid-template-columns: 1fr 1fr 1fr;
  gap: 20px;
}
</style>
