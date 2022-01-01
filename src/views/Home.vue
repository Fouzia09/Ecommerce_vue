<template>
  <div class="home">
  <LisProduct :data="all_product"/>
  </div>
</template>

<script>
// @ is an alias to /src
  import BDD from '../BDD'
  import LisProduct from '../components/ListProduct.vue'



export default {
  name: 'Home',
  components: { LisProduct },

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
        constructor(id,name, model, price, img, detail) {
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
          const new_product = new Product(product.id, product.name, product.model, product.price, product.img, product.detail)

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
