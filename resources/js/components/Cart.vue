<template>
    <div>
        <li class="nav-item">
            <a href="/checkout" 
                class="btn btn-warning btn-sm">
                Cart {{itemCount}}
            </a>
        </li>
    </div>
</template>

<script>
    export default {
        data(){
            return {
                itemCount: '',
            }
        },
        mounted() {
            this.$root.$on('changeInCart', (item) => {
                this.itemCount = item;
            })
        },
        methods:{
            async getCartItemsOnPageLoad(){
                let resp = await axios.post('/cart');
                this.itemCount = resp.data.items
                // alert(this.itemCount);
            }
        },
        created(){
            this.getCartItemsOnPageLoad();
        }
    }
</script>
