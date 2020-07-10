<template>
    <div>
        <div class="nav-bar "></div>
        <h1> {{ title }}</h1>
        <div id="app">
            <product :premium="premium"></product>
            <product :premium="premium"></product>

            <p>Shipping: {{ shipping}}</p>


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
                premium: true
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
