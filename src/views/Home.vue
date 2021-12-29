<template>
  <div class="home">
    <ListProduct />
  </div>
</template>

<script>
// @ is an alias to /src
import ListProduct from '@/components/ListProduct.vue'

export default {
  name: 'Home',
  components: { ListProduct }
}
</script>
