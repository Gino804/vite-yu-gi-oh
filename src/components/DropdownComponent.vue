<script>
export default {
    props: {
        defaultValue: String,
        label: String,
        options: Array
    }
}
</script>

<template>
    <label for="dropdown">{{ label }}</label>
    <select id="dropdown">
        <option value="default">{{ defaultValue }}</option>
        <option v-for="option in options" :value="option">{{ option }}</option>
    </select>
</template>

<style>
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