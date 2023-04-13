<template>
    <div>
        <loading v-if="loading" />
        <div class="h-screen" v-else>
            <div class="flex justify-center items center py-[1%]">
                <p class="text-6xl font-bold">PokeDEx</p>
            </div>
            <div class="pl-[5%]"><input type="text" class="border-solid border-2 border-green-100 bg-green-50 mt-[2%]"></div>
            <div class="my-[2%] flex flex-wrap px-[5%] h-[80%]">
                <Card v-for="i in posts" :key="i.name" :nombre="i.name" :url="i.url" class="mx-[0.5%] my-[0.5%]" />
            </div>
        </div>
    </div>
</template>
<script>
export default {
    data() {
        return {
            count: 0,
            posts: [],
            poke: {},
            loading: true
        };
    },
    mounted() {
        this.getInfo();
        this.getImages();
    },
    methods: {
        async getInfo() {
            const { data } = await this.$axios.get("pokemon");
            this.count = data.count;
        },
        async getImages() {
            for (let i = 1; i < 500; i++) {
                let datos = await this.$axios.get(`pokemon/${i}`);
                this.poke.url = datos.data.sprites.other.home.front_default;
                this.poke.name = datos.data.name;
                this.posts.push(this.poke);
                this.poke = {};
                console.log(datos.data.sprites.front_default);
            }
            this.loading = false
        }
    },
}
</script>
<style></style>
