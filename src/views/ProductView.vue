<template>
  <div class="m-4">
    <table class="table table-bordered">
      <tr>
        <td class="fw-bold">Название</td>
        <td class="fst-italic">{{product.title}}</td>
      </tr>
      <tr>
        <td class="fw-bold">Фотка</td>
        <td class="fst-italic"><img class="img-fluid" :src="product.images[0]" alt=""></td>
      </tr>
      <tr>
        <td class="fw-bold">Описание</td>
        <td class="fst-italic">{{product.description}}</td>
      </tr>
      <tr>
        <td class="fw-bold">Рейтинг: </td>
        <td class="fst-italic">{{product.rating}}</td>
      </tr>
      <tr>
        <td class="fw-bold">Цена: </td>
        <td class="fst-italic">{{product.price}}$</td>
      </tr>
    </table>
    <RouterLink class="btn btn-dark m-1" to="/products">Назад</RouterLink>
  </div>





</template>

<script>
  export default {
    data() {
      return {
        product: null,
        id: null,
      }
    },
    created() {
      this.id = this.$route.params.id;
      const url = 'https://dummyjson.com/products/' + this.id;
      fetch(url)
          .then( response => response.json())
          .then( data => this.product = data )
    }
  }
</script>