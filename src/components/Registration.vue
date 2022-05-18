<template> 
    <div class="container mt-5">
        <h3>Registrarme</h3>
        <form @submit.prevent="dataValidation"
                action=""
                method="POST"
                class="mt-3"
                >
                    <label for="email" class="form-label text-start">Email</label>
                    <input type="email" class="form-control" id="email" placeholder="tu@email.com" v-model="email">
                    <br>
                    <label for="password" class="form-label text-start">Contraseña</label>
                    <input type="text" class="form-control" id="password" v-model="password">
                    <br>
                    <input type="submit" class="btn btn-warning" value="Registrarme">
                    <br>
        </form>
        <div v-if="errors.length > 0" class="mt-3">
            <ul class="text-danger fw-bold list-unstyled">
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
            email: "",
            password: "",
        }
    },
    methods: {
        dataValidation () {
            if (this.email && this.password) {
                return true
            };
            if (this.email === "") {this.errors.push("Ingresá un email.")};
            if (this.password === "") {this.errors.push("Ingresá una contraseña.")};
        }
    }
}
</script>