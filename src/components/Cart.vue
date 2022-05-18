<template>
    <div class="">
        <div class="cart-container">
            <img src="../assets/carrito.png" alt="Carrito">
            <div class="cart-counter">
                <p class="text-warning">{{products.length}}</p>
            </div>        
        </div>
    </div>
</template>

<script>
export default {
    name: "Cart",
    props: {
        products: {
            type: Array,
            required: true,
        },
    },
}
</script>

<style>
    .cart-container{
        position: fixed;
        top: 15px;
        right: 0;
        display: inline-block;
        text-align: center;
    }
    .cart-counter{
        position: absolute;
        top: 50%;
        left: 50%;
        transform: translate(-50%, -50%);
    }
</style>