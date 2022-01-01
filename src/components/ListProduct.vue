<template>
  <div class="container">
    <div class="card" style="width: 18rem; height: 25rem" v-for="product of data" :key="product.id">
      <img :src="product.img" alt="">
      <div class="card-body">
        <ul class="list-group">
          <span>{{ product.id }}</span>
          <span>{{ product.name }}</span>
          <span>{{ product.model }}</span>
          <span>{{ product.price }}</span>
          <button @click="goToArticle(product.id)" type="button" class="btn btn-primary" >Detail</button>
        </ul>
      </div>
    </div>

  </div>
</template>

<script>

 


export default {
  components: {
     
  },
  props: {
    data: Object
  },
  methods: {
    goToArticle (prodId) {
    let proId=prodId
      this.$router.push({ name: 'Detail', params: { id: proId} })
    
    }
   
  },
    // methods: {
    //   getDetail(articleNumber) {
    //     console.log(articleNumber)
    //     this.$router.push({
    //       name: 'product',
    //       params: {
    //         id: articleNumber
    //       }
    //     })
    //   }
    // },
  }
</script>

<style>
  div.container {
    display: flex;
    flex-wrap: wrap;
    justify-content: center;
  }

  .card {
    margin: 10px;
  }

  ul {
    margin-top: 10px;
    margin-bottom: 10px;
  }

  span:last-of-type {
    margin-bottom: 10px;
  }

  .btn {
    width: 120px;
    margin: auto;
  }
</style>