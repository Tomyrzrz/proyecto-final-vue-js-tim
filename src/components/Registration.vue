<template> 
    <div class="container">
        <form @submit.prevent="dataValidation"
                action=""
                method="POST">
                    <label for="email" class="form-label text-start">Email</label>
                    <input type="email" class="form-control" id="email" placeholder="tu@email.com">
                    <br>
                    <label for="password" class="form-label text-start">Contraseña</label>
                    <input type="text" class="form-control" id="password">
                    <br>
                    <input type="submit" class="btn btn-warning" value="Registrarme">
                    <br>
        </form>
        <div v-if="errors.length > 0">
            <ul class="text-danger fw-bold">
                <li v-for="(error, i) in errors" :key="i">{{error}}</li>
            </ul>
        </div>
    </div>
</template>

<script>
export default {
    name: "Registration",
    data() {
        return {
            errors: [],
        }
    },
    methods: {
        dataValidation: ()=> {
            if (this.email && this.password) {
                return true
            };
            if (this.email === "") {this.errors.push("Ingresá un email.")};
            if (this.password === "") {this.errors.push("Ingresá una contraseña.")};
            console.log(errors)
        }
    }
}
</script>

<style>

</style>