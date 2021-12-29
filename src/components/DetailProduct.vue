<template>

    <div class="card" style="width: 18rem; height: 25rem">
        <ul class="list-group">
            <li class="list-group-item">{{ detail_product.detail.designation }}</li>
            <li class="list-group-item">{{ detail_product.detail.memoire }}</li>
            <img :src="detail_product.detail.img" alt="">
        </ul>
    </div>


</template>

<script>
    export default {
        components: {

        },
        props: {
            detail_product: Object
        }

    }
</script>

<style>

</style>