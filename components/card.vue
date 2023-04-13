<template >
    <nuxt-link :to="nombre" class="w-[18%] h-[1/2] bg-gray-200 flex flex-col justify-center items-center rounded-full border-solid border-2 border-black py-[1%]" style="background: linear-gradient(146deg, rgba(255,0,0,1) 45%, rgba(0,0,0,1) 47%, rgba(255,255,255,1) 49%);">
    <div class=" flex flex-col justify-center items-center pb-[10%]">
        <img :src="url" class="px-[15%]"
            >
        <p>{{ nombre }}</p>
    </div></nuxt-link>
</template>
<script>
export default {
    name: 'card',
    props: {
        nombre: {
            type: String,
            required: true
        },
        url: {
            type: String,
            required: true
        }
    }
}
</script>
<style></style>
    