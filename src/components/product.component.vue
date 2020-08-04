<template>
        <div class="product-card">
            <img :src="product.productImageUrl" class="product-image">
            <br >
            <span>{{product.productName | capitalizeText}}</span>
            <br >
            <span>In stock: {{product.isInStock}}</span>
            <br > 
            <span>{{product.price}} {{product.currency}}</span>
            <br>
            <button type="button" @click="addToCart(product)">Add to cart</button>
        </div>
</template>

<script>
export default {
    props: ["productModel"],
    data() {
        return {
            product: this.productModel
        }
    },
    methods:{
        addToCart(productValue){
            this.$emit('product-added-to-cart', productValue);
        }
    },
    filters:{
        capitalizeText: function(text){
            return text.toLowerCase();
        }
    }
    
}
</script>