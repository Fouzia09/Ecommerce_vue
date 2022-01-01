<template>
  <div class="home">
    <nav class="navbar navbar-light bg-light">
      <div class="container-fluid">
        <router-link to="/">Home</router-link>
        <div class="wrapper-input">
          
          <form class="d-flex">
            <input class="form-control me-2" type="search" placeholder="Search" aria-label="Search" v-model="searchUser">
          </form>
          <div class="search">
            <router-link to="/produit">
            <div v-for="(product, i) in search_product" :key="i" class="container">
              <p>{{product.name}}</p>
            </div>
            </router-link>
          </div>
        </div>
      </div>
    </nav>

    <LisProduct :data="all_product" />

  </div>
</template>

<script>
  // @ is an alias to /src
  import BDD from '../BDD'
  import LisProduct from '../components/ListProduct.vue'
  import {
    ref,
    watch

  } from 'vue'



  export default {
    name: 'Home',
    components: {
      LisProduct
    },

    methods: {
      goToArticle() {

        this.$router.push('Details')
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

    setup() {
      class Product {
        constructor(id, name, model, price, img, detail) {
          this.id = id
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
          const new_product = new Product(product.id, product.name, product.model, product.price, product.img, product
            .detail)

          // make all restaurant array
          all_product.push(new_product);

        }
        console.log(all_product)
      };

      // User search product
      const searchUser = ref("");
      let search_product = ref([]);
      watch(searchUser, new_value => {
        let regex = RegExp(new_value.toLowerCase());
        let new_search_product = all_product.filter(product => regex.test(product.name.toLowerCase()));
        new_value == 0 ? search_product.value = [] : search_product.value = new_search_product;

      })
      //
      //
      makeData();
      // return
      return {
        all_product,
        searchUser,
        search_product,
      }
    }

  }
</script>

<style scoped>

.wrapper-input {
  position: relative;
}
.search {
  width: 100%;
  position: absolute;
  top: 100%;
  background-color: #ffffff;
  z-index: 10;
}
</style>