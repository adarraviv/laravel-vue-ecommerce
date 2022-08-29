<template>
    <div>
        <hr>
        <!-- <button class="btn btn-warning">Add to Cart</button> -->
        <button class="btn btn-warning" v-on:click.prevent="addProductToCart()">Add to Cart</button>
    </div>
</template>

<script>
    export default {
        data(){
            return{
                data: ''
            }
        },
        props:['productId','userId'],
        methods:{
            async addProductToCart(){
                // alert(this.productId);
                // Checking if user logged in.
                if(this.userId == 0){
                    this.$toastr.e("You Need to login, to ass this product in cart.");
                    return;
                }

                // If user logged in then add item to cart

                let resp = await axios.post('/cart', {
                    'product_id': this.productId
                });

                this.$root.$emit('changeInCart', resp.data.items);
            }
        },
        mounted() {
            console.log('Component mounted.')
        }
    }
</script>
