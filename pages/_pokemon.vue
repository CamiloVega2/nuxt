<template>
    <div class="h-screen">
        <div class="flex justify-center text-4xl">
            <p>{{ nombre.toUpperCase() }}</p>
        </div>
        <div class="h-[95%] flex flex-col justify-center mx-[5%]" style="background: linear-gradient(90deg, rgba(255,0,0,1) 45%, rgba(0,0,0,1) 47%, rgba(255,255,255,1) 49%);">
            <div class="flex justify-center">
                <img :src="img1" class="h-[250px] w-[250px]">
                <img :src="img2" class="h-[250px] w-[250px]">
            </div>
            <div class="flex justify-center">
                <img :src="img3" class="h-[250px] w-[250px]">
                <img :src="img4" class="h-[250px] w-[250px]">
            </div>
        </div>
    </div>
</template>
<script>
export default {
    name: 'PokemonPage',
    data() {
        return {
            nombre: "",
            img1: "",
            img2: "",
            img3: "",
            img4: "",
        }
    },
    mounted() {
        this.getInformation()
    },
    methods: {
        async getInformation() {
            const information = await this.$axios.get(`pokemon/${this.$route.params.pokemon}`)
            console.log(information);
            this.nombre = information.data.name
            this.img1 = information.data.sprites.front_default
            this.img2 = information.data.sprites.back_default
            this.img3 = information.data.sprites.front_shiny
            this.img4 = information.data.sprites.back_shiny
        }
    },
}
</script>
<style></style>