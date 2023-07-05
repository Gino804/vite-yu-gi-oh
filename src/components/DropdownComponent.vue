<script>
export default {
    data() {
        return {
            selectedOption: 'default'
        }
    },

    props: {
        defaultValue: String,
        label: String,
        options: Array
    },

    emits: ['changed']
}
</script>

<template>
    <label for="dropdown">{{ label }}</label>
    <select id="dropdown" @change="$emit('changed', selectedOption)" v-model="selectedOption">
        <option value="default">{{ defaultValue }}</option>
        <option v-for="option in options" :key="option" :value="option">{{ option }}</option>
    </select>
</template>

<style scoped>
select {
    padding: 5px;
    border-radius: 5px;
    border: 1px solid black;
}

label {
    margin-right: 5px;
    font-size: 14px;
}
</style>