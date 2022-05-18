<template>
    <div class="card m-1 align-items-center">
        <img :src="getImgUrl()" class="card-img-top d-block w-50" :alt="tittle">
        <div class="card-body">
            <h5 class="card-title text-center">{{tittle}}</h5>
            <p class="card-text text-center">{{description}}</p>
            <p class="card-text text-center">$ {{price}}</p>
            <div class="d-flex flex-column align-items-center">
                <div class="d-flex flex-row align-items-center">
                    <button @click="decrease()" :class="['btn', quantity <1 ? 'btn-secondary disabled' : 'btn-secondary']" class="m-2">-</button>
                    <p class="m-2">{{quantity}}</p>
                    <button @click="increase()" class="btn btn-secondary m-2">+</button>    
                </div>
                <button type="button" class="btn btn-warning m-2" @click="addToCart()">Agregar</button>
            </div>            
        </div>
    </div>
</template>

<script>
export default {
    name: "Products",
    props: {
        tittle: {
            type: String,
            required: true,
        },
        description: {
            type: String,
            required: true,
        },
        price: {
            type: Number,
            required: true,
        },
        photo: {
            type: String,
            required: true,
        },
        id: {
            type: Number,
            required: true,
        },
        category: {
            type: String,
            required: false,
        },
        quantity: {
            type: Number,
            required: true,
        }
    }, 
    methods: {
        getImgUrl() {
            return require(`@/assets/products/${this.photo}`);
        },
        increase() {
            this.quantity = this.quantity+1
        },
        decrease() {
            this.quantity = this.quantity-1
        },
        addToCart() {
            this.$emit("add-to-cart", this.id);
        },
    },
}
</script>