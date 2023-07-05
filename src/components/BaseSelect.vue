<script>
export default {
    props: {
        defaultLabel: String,
        options: Array
    },
    data() {
        return {
            selectedOption: ''
        }
    },
    emits: ['option-change'],

}
</script>



<template>
    <select v-model="selectedOption" @change="$emit('option-change', selectedOption)" class="form-select">
        <option value="">{{ defaultLabel || '--' }}</option>
        <option v-for="option in options" :key="option">{{ option }}</option>
    </select>
</template>



<style lang="scss" scoped>
select {
    width: 25%;
    margin: 50px auto;
}
</style>

