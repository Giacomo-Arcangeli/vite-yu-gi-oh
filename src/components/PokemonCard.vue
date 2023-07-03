<script>
export default {
    props: {
        name: String,
        type: String,
        image: String
    }
}
</script>



<template>
    <div class="pok-card text-center mt-2">
        <img :src="image" alt="" srcset="">
        <h4 class="my-2">{{ name }}</h4>
        <div>{{ type }}</div>
    </div>
</template>



<style lang="scss">
.pok-card {
    padding: 10px;
    background-color: azure;
    box-shadow: 5px 5px 10px rgb(179, 179, 179);
    border-radius: 10px;
}

img {
    width: 100%;
    height: 200px;
}
</style>