<template>
    <div>
        <hr>
        <button class="btn btn-warning" v-on:click.prevent="addProductToCart()">Add to Cart</button>
    </div>
</template>

<script>
    export default {
        data(){},
        props:['productId','userId'],
        methods:{
            addProductToCart(){
                alert(this.productId);
            }
        },
        mounted() {
            console.log('Component mounted.')
        }
    }
</script>
