<template>
    <div id="app">
        <div class="header d-flex flex-column align-items-center m-2">
            <img alt="3P logo" src="./assets/3p-logo.png">
            <h1>Pizzas, pastas y postres</h1>
            <h2>Todo rico y casero</h2>
        </div>
        <Cart :products="productsInCart"/>
        <div class="row row-cols-1 row-cols-md-3 justify-content-center">
            <Products 
                v-for="(product, i) in products" :key="i"
                    :id="product.id"
                    :tittle="product.tittle"
                    :description="product.description"
                    :price="product.price"
                    :photo="product.photo"
                    @add-to-cart="addToCart"
            />
        </div>
        <Registration/>
    </div>
</template>

<script>

import Products from './components/Products.vue';
import Cart from './components/Cart.vue';
import Registration from './components/Registration.vue';

export default {
    name: "App",
    components: {
        Products,
        Cart,
        Registration,
    },
    data() {
        return {
            products: [
                {id: 1, tittle: "Pizza con almendras", description: "Pizza con salsa de tomate, queso mozzarella premium, pimientos rojos y verdes y almendras tostadas.", price: 999, photo: "pizzas/pizza-almendras.png", category: "pizzas"},
                {id: 2, tittle: "Pizza con carne", description: "Pizza con salsa de tomate, queso mozzarella premium, pimientos rojos, amarillos y verdes en cubos y trocitos de carne de ternera al horno.", price: 1999, photo: "pizzas/pizza-carne.png", category: "pizzas"},
                {id: 3, tittle: "Pizza Margarita", description: "Pizza con salsa de tomate, queso mozzarella premium y albahaca fresca, con reducción de aceite de oliva.", price: 899, photo: "pizzas/pizza-margarita.png", category: "pizzas"},
                {id: 4, tittle: "Pizza con morrones", description: "Pizza con salsa de tomate, queso mozzarella premium y morrones rojos asados.", price: 1099, photo: "pizzas/pizza-morrones.png", category: "pizzas"},
                {id: 5, tittle: "Pizza con tomates", description: "Pizza con salsa de tomate, queso cuartirolo y tomates cherry confitados.", price: 799, photo: "pizzas/pizza-tomates.png", category: "pizzas"}, 
            ],
            productsInCart: [],
        }
    },
    methods: {
        addToCart(id) {
            let result = this.products.find((item) => {
                return item.id == id;
            });
            this.productsInCart.push(result);
        }
    },
}
</script>

<style>
#app {
    font-family: 'Lucida Sans', 'Lucida Sans Regular', 'Lucida Grande', 'Lucida Sans Unicode', Geneva, Verdana, sans-serif;
}
img {
    width: 10%;
}
</style>
