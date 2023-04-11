<template>
    <div class="h-screen">
        <div class="flex justify-center items center py-[1%]">
            <p class="text-6xl font-bold">PokeDEx</p>
        </div>
        <div><input type="text" class="border-solid border-2 border-green-100 bg-green-50 mt-[2%]"></div>
        <div class="my-[2%] flex flex-wrap px-[5%] h-[80%] ">
            <p>{{ data }}</p>
            <Card v-for="i in posts" :key="i" :nombre="i.name" :url="i.url" class="mx-[0.5%] my-[0.5%]"/>
        </div>
    </div>
</template>
<script>
export default {
    data() {
        return {
            posts: []
        };
    },
    mounted(){
        this.getInfo()
    },
    methods: {
    async getInfo(){
          const {data} = await  this.$axios.get('pokemon')
          this.posts = data.results
          console.log(data);
        },
    },
}
</script>
<style></style>