<template>
  <div class="container">
    <div class="card" style="width: 18rem; height: 25rem" v-for="product of all_product" :key="product.id">
      <img :src="product.img" alt="">
      <div class="card-body">
        <ul class="list-group">
          <span>{{ product.id }}</span>
          <span>{{ product.name }}</span>
          <span>{{ product.model }}</span>
          <span>{{ product.price }}</span>
          <button @click="goToArticle(number)" type="button" class="btn btn-primary" >Detail</button>
        </ul>
      </div>
    </div>
    <DetailProduct v-for="(data, i ) in all_product" :key="i" :detail_product="data" />
  </div>
</template>

<script>
  import BDD from '../BDD'
  import DetailProduct from '@/components/DetailProduct'


  export default {
    components: {
      DetailProduct
    },
  methods: {
    goToArticle () {
   
      this.$router.push('Details')
    }
  },
    props: {
      number: String,
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
    setup() {
      class Product {
        constructor(name, model, price, img, detail) {
          this.name = name
          this.model = model
          this.price = price
          this.img = img
          this.detail = detail
        }
      }

      let all_product = [];
      const makeData = () => {

        for (const product of BDD) {
          const new_product = new Product(product.name, product.model, product.price, product.img, product.detail)

          // make all restaurant array
          all_product.push(new_product);

        }
        console.log(all_product)
      };
      //
      makeData();
      // return
      return {
        all_product,


      }
    }
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