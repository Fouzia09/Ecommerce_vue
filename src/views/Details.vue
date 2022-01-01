<template>
	<div class="details">
		<div class="container">
			<div class="row">
				<div class="col-md-12" v-for="infos of BDD" :key="infos.id"> 
					<div v-if="proId == infos.id">
						<p>{{ infos.detail.designation }}</p>
            <h4>{{ infos.detail.memoire}}</h4>
						<img :src="infos.detail.img"  class="img-fluid">
					</div>
				</div>
			</div>
		</div>
	</div>
</template>

<script>
  import BDD from '../BDD'
  export default {
    components: {

    },
    data() {
      return {
        proId:this.$route.params.id,
      }
    },
    setup() {

      return {
        BDD
      }
    }
  }
</script>