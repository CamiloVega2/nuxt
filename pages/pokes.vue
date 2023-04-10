<template>
    <div class="h-screen">
        <div class="flex justify-center items center py-[1%]">
            <p class="text-6xl font-bold">PokeDEx</p>
        </div>
        <div><input type="text" class="border-solid border-2 border-green-100 bg-green-50 mt-[2%]"></div>
        <div class="my-[2%] flex flex-wrap gap-[2%] h-[75%] px-[5%]">
            <Card />
            <Card />
            <Card />
            <Card />
            <Card />
            <Card />
            <Card />
            <Card />
            <Card />
            <Card />
        </div>
    </div>
</template>
<script>
import Card from '~/components/card.vue';

export default {
    components: { Card },
    methods: {
    },

    data() {
        return {
            name:'camilo',
            posts: []
        }
    },
    async fetch() {
        posts = await fetch('https://pokeapi.co/api/v2/').then(results = results.json())
    },
    created(){
        console.log(this.posts);
    }
}
</script>
<style></style>