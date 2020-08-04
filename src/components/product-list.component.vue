<template>
    <div class="products-container">
        <div v-for="product in products" :key="product.id">
            <ProductComponent :productModel="product" v-on:product-added-to-cart="onProductAdded($event)"></ProductComponent>
        </div>
        
    </div>
</template>

<script>
import ProductComponent from './product.component';

export default {
    components: { ProductComponent },
    data() {
        return {
            products: [],
            productsInCart: [],
            count: 0
        }
    },
    computed:{
        productsInCartCount() {
            let result = 0;
            for(let i = 0; i < this.productsInCart.length; i++){
                result += this.productsInCart[i].quantity;
            }

            return result;
        }
    },
    watch:{
        productsInCart: {
            deep: true,
            handler(newVal){
                if(newVal && newVal.length){
                    this.count = 0;
                    for(let i = 0; i < newVal.length; i++){
                        this.count += newVal[i].quantity;
                    }
                }
            }
        },

        "productsInCart.length"(newVal){
            console.log(newVal);
        }
    },
    methods: {
        getProducts(){
            fetch("http://ll-internship-vue-trainig.azurewebsites.net/api/GetProducts?code=Ce/izgSOfZr5Yz9ZxwE1cZLv2MWGm0bRXmOSklhx7U9ieWnc1Na24w==")
            .then(result => result.json())
            .then(prods => this.products = prods);
        },
        onProductAdded(productValue){
            if(this.productsInCart.includes(productValue)) {
                let product = this.productsInCart.find(p => p.id == productValue.id);
                product.quantity += 1;
            } else{
                productValue.quantity = 1;
                this.productsInCart.push(productValue);
            }
        }
    },

    created() {
        this.getProducts();
        
    }
}
</script>

<style>
</style>