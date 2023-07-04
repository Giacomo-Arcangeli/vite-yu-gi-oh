<script>
export default {
    data() {
        return {
            types: [
                "Bug",
                "Dark",
                "Dragon",
                "Electric",
                "Fairy",
                "Fighting",
                "Fire",
                "Flying",
                "Ghost",
                "Grass",
                "Ground",
                "Ice",
                "Normal",
                "Poison",
                "Psychic",
                "Rock",
                "Steel",
                "Water"
            ]
        }
    }
}
</script>



<template>
    <select class="form-select">
        <option v-for="type in types">{{ type }}</option>
    </select>
</template>



<style lang="scss" scoped>
select {
    width: 50%;
    margin: 50px auto;
}
</style>

