<template>
    <div>
        <div class="nav-bar "></div>
        <h1> {{ title }}</h1>
        <div id="app">
            <div class="cart ">


                <p>Cart {{ cart.length }}</p>
            </div>


            <product :premium="premium" @add-to-cart="updateCart"></product>




        </div>
    </div>


</template>
<script>

    import Product from "@/components/product";


    export default {
        name: 'HelloWorld',
        components: {Product},
        el: '#app',
        data: function () {
            return {
                premium: false,
                cart: [],



            };
        },
        methods:{
            updateCart(id){
                this.cart.push(id)
            }
        },


        computed: {



        }
    }

</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style>

</style>
