<template>
    <div id="app">
        <div class="header d-flex flex-column align-items-center m-2">
            <img alt="3P logo" src="./assets/3p-logo.png">
            <h1>Pizzas, pastas y Ensaladas</h1>
            <h2>Todo rico y casero hecho al momento</h2>
        </div>
        <Cart :totalOfProducts="totalizeProducts"/>
        <div class="row row-cols-1 row-cols-md-3 justify-content-center">
            <Products 
                v-for="(product, i) in products" :key="i"
                    :id="product.id"
                    :tittle="product.tittle"
                    :description="product.description"
                    :price="product.price"
                    :photo="product.photo"
                    :quantity="product.quantity"
                    @add-to-cart="addToCart"
            />
        </div>
        <Registration/>
        <Login/>
    </div>
</template>

<script>

import Products from './components/Products.vue';
import Cart from './components/Cart.vue';
import Registration from './components/Registration.vue';
import Login from './components/Login.vue';

export default {
    name: "App",
    components: {
        Products,
        Cart,
        Registration,
        Login,
    },
    data() {
        return {
            products: [
                {id: 1, tittle: "Pizza con almendras", description: "Pizza con salsa de tomate, queso mozzarella premium, pimientos rojos y verdes y almendras tostadas.", price: 999, photo: "pizzas/pizza-almendras.png", category: "pizzas", quantity:0},
                {id: 2, tittle: "Pizza con carne", description: "Pizza con salsa de tomate, queso mozzarella premium, pimientos rojos, amarillos y verdes en cubos y trocitos de carne de ternera al horno.", price: 1999, photo: "pizzas/pizza-carne.png", category: "pizzas", quantity:0},
                {id: 3, tittle: "Pizza Margarita", description: "Pizza con salsa de tomate, queso mozzarella premium y albahaca fresca, con reducción de aceite de oliva.", price: 899, photo: "pizzas/pizza-margarita.png", category: "pizzas", quantity:0},
                {id: 4, tittle: "Pizza con morrones", description: "Pizza con salsa de tomate, queso mozzarella premium y morrones rojos asados.", price: 1099, photo: "pizzas/pizza-morrones.png", category: "pizzas", quantity:0},
                {id: 5, tittle: "Pizza con tomates", description: "Pizza con salsa de tomate, queso cuartirolo y tomates cherry confitados.", price: 799, photo: "pizzas/pizza-tomates.png", category: "pizzas", quantity:0}, 
            ],
            productsInCart: [],
            
        }
    },
    methods: {
        addToCart(id) {
            let productAdded = this.productsInCart.find((item) => {
                return item.id == id;
            });
            if (productAdded != null) {
                productAdded.quantity++; //Aquí debiera sumar la cantidad que agregó el usuario 
            }
            else {
                let newProduct = this.productsInCart.find((item) => {
                return item.id == id;});    
                let newCopy = {...newProduct, quantity: 1}; //Aquí debiera sumar la cantidad que agregó el usuario
                this.productsInCart.push(newCopy);
            }
        },
    },
    computed: {
        totalizeProducts() {
            return this.productsInCart.map(products => products.quantity).reduce((prev, curr) => prev + curr, 0)
        },
    }
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
