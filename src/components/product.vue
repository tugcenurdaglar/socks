<template>
    <div id="product">
        <div class="row p-2">

            <div class="col-md-4">
                <div class="product-image">
                    <img :src="image" :alt="altText"></div>
                <h5 v-show="inventory ">In Stock</h5>

            </div>

            <div class="col-md-4">
                <div class="product-info">
                    <h1>{{ product }}</h1>
                    <h1>{{ title }}</h1>
                    <p> Shipping: {{ shipping }}</p>


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
                    <button v-on:click="addToCart"
                            :disabled="!inStock"
                            :class="{ disabledButton:!inStock }"
                    >Add to Cart

                    </button>


                </div>


            </div>

            <div class="col-md-4">


            </div>


        </div>
    </div>
</template>

<script>
    export default {
        name: "product",
        props: {
            premium: {
                type: Boolean,
                required: true,

            }
        },
        data(){
            return{
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




            }
        },
        methods:{
            addToCart(){
              this.$emit('add-to-cart',this.variants[this.selectedVariant].variantId)
            },

            updateProduct(index) {
                this.selectedVariant = index
                console.log(index)
            },


        },
        computed:{
            title() {
                return this.brand + ' ' + this.product
            },
            image(){
                return this.variants[this.selectedVariant].variantImage

            },

            inStock(){
                return this.variants[this.selectedVariant].variantQuantity

            },
            shipping(){
                if (this.premium){
                    return "Free"
                }else {
                    return  2.99
                }
            }

        }


    }
</script>

<style scoped>

</style>