<template>
    <div>
        <div class="nav-bar "></div>
        <h1> {{ title }}</h1>
        <div id="app">


            <product :premium="premium"></product>




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



            };
        },


        computed: {
            title() {
                return this.brand + ' ' + this.product
            },


        }
    }

</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style>

</style>
