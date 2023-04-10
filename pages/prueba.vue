<template>
    <div>
        <p>{{ nombre }}</p>
        <img src="https://encrypted-tbn0.gstatic.com/images?q=tbn:ANd9GcQP-Edh4XPc220e7GXISteTInlPeJa2sRdSlQ&usqp=CAU" v-if="mostrar == true">
        <button @click="cambiar" class="bg-red-500">Cambiar Nombre</button>
    </div>
</template>

<script>
export default {
    name: "PruebaPage",
    data() {
        return {
            nombre: 'Juan Camilo',
            mostrar: true,
        }
    },
    methods: {
        cambiar() {
            if (this.mostrar == true) {
                this.nombre = 'Vega Vega'
                this.mostrar = false
            } else {
                this.nombre = 'Juan Camilo'
                this.mostrar = true
            }
        }
    }
};
</script>
<style></style>
