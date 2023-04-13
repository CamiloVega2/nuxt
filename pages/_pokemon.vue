<template>
    <div style="background-image: url('https://tiermaker.com/images/templates/3904221589914255.jpg');" class="bg-auto bg-no-repeat bg-center">
        <loading v-if="loading" />
        <div class="h-screen">
            <div class="flex justify-center text-4xl">
                <p>{{ nombre.toUpperCase() }}</p>
            </div>
            <div class=" flex flex-col justify-center mx-[5%]">
                <div class="flex justify-center">
                    <img :src="img1" class="h-[250px] w-[250px]">
                    <img :src="img2" class="h-[250px] w-[250px]">
                </div>
                <div class="flex justify-center">
                    <img :src="img3" class="h-[250px] w-[250px]">
                    <img :src="img4" class="h-[250px] w-[250px]">
                </div>
                <div class="flex  flex-col items-center">
                    <p>HP: {{ hp }}</p>
                    <p>ATTACK: {{ attack }}</p>
                    <p>DEFENSE: {{ defense }}</p>
                    <p>ATTACKSPECIAL: {{ attackspcl }}</p>
                    <p>DEFENSESPECIAL: {{ defensespcl }}</p>
                    <p>SPEED: {{ speed }}</p>
                </div>
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
            hp: "",
            attack: "",
            defense: "",
            attackspcl: "",
            defensespcl: "",
            speed: "",
            type:"",
            loading: true
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
            this.hp = information.data.stats[0].base_stat
            this.attack = information.data.stats[1].base_stat
            this.defense = information.data.stats[2].base_stat
            this.attackspcl = information.data.stats[3].base_stat
            this.defensespcl = information.data.stats[4].base_stat
            this.speed = information.data.stats[5].base_stat
            this.type = information.data.types[0].name
            this.loading = false
        }
    },
}
</script>
<style></style>