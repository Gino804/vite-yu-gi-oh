<script>
export default {
    props: {
        image: String,
        number: Number,
        name: String,
        type: String
    }
}
</script>

<template>
    <div class="card">
        <img :src="image" :alt="name">
        <p>{{ number }}</p>
        <h4>{{ name }}</h4>
        <p><i>{{ type }}</i></p>
    </div>
</template>

<style scoped>
.card {
    background-color: white;
    border-radius: 15px;
    text-align: center;
    padding: 15px 0;
}

img {
    width: 150px;
    height: 150px;
    border-radius: 50%;
}

h4 {
    margin: 5px 0;
}
</style>