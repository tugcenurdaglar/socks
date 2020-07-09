<template>
    <div>
        <div class="nav-bar "></div>
        <h1> {{ title }}</h1>
        <div id="app">


            <div class="row p-2">

                <div class="col-md-4">
                    <div class="product-image">
                        <img :src="image" :alt="altText"></div>
                    <h5 v-show="inventory ">In Stock</h5>

                </div>

                <div class="col-md-4">
                    <div class="product-info">

                        <div class="row">
                            <ul>
                                <li v-for="detail in details" :key="detail">{{ detail }}</li>
                            </ul>
                        </div>


                        <div class="row p-3">
                            <div class="color-box "
                                 v-for="(variant,index) in variants"
                                 :key="variant.variantId"
                                 :style="{backgroundColor: variant.variantColor }"
                                 @mouseover="updateProduct(index)"
                            ></div>
                        </div>


                    </div>


                </div>

                <div class="col-md-4">
                    <div class="cart ">
                        <button v-on:click="addToCart"
                                :disabled="!inStock"
                                :class="{ disabledButton:!inStock }"
                                >Add to Cart

                        </button>

                        <p>Cart {{ cart }}</p>
                    </div>
                </div>


            </div>


        </div>
    </div>

</template>

<script>
    export default {
        name: 'HelloWorld',

        data: () => ({

            product: 'Socks',
            brand:'HM',
            selectedVariant:0,
            
            details: ["80% cotton", "20% polyester", "Gender-neutral"],
            variants: [
                {
                    variantId: 2234,
                    variantColor: "green",
                    variantImage: "./images/vmSocks-green-onWhite.jpg",
                    variantQuantity:10,
                },
                {
                    variantId: 2235,
                    variantColor: "blue",
                    variantImage: "./images/vmSocks-blue-onWhite.jpg",
                    variantQuantity:0,


                }

            ],
            cart: 0,


        }),
        methods: {
            addToCart() {
                this.cart += 1;
            },
            updateProduct(index) {
                this.selectedVariant = index
                console.log(index)
            }
        },
        computed:{
            title(){
                return this.brand+ ' '+this.product
            },
            image(){
                return this.variants[this.selectedVariant].variantImage

            },
            inStock(){
                return this.variants[this.selectedVariant].variantQuantity

            }
        }
    }

</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style>

</style>
