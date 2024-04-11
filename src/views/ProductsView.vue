<template>
  <section class="bg-gradient bg-danger">
    <h2>Товары для чайников</h2>
    <div class="d-flex flex-wrap justify-content-center p-4">
      <div v-for="product in products" class="card m-2">
        <div class="card-header">{{ product.title }}</div>
        <div class="card-body">
          <img class="img-fluid" :src="product.thumbnail" :alt="product.title">
        </div>
        <div class="card-footer d-flex justify-content-between align-items-center">
          <div class="fw-bold fst-italic">Цена: {{product.price}}$</div>
          <div>
            <RouterLink class="btn btn-dark" :to="'/products/' + product.id">Подробнее</RouterLink>
          </div>
        </div>
      </div>
    </div>
  </section>
</template>

<script>
  export default {
    //Переменные
    data(){
      return {
        products: [],
      }
    },
    // Методы
    methods: {
      getProducts(){
        fetch('https://dummyjson.com/products')
            .then(response => response.json())
            .then(data => this.products = data.products)
      }
    },
    // Метод выполняется при загрузке страницы
    created() {
      this.getProducts();
    }
  }
</script>

<style scoped>
  .card {
    min-width: 300px;
  }
</style>