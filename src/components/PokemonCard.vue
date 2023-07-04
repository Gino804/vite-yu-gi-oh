<script>
export default {
    props: {
        image: String,
        number: Number,
        name: String,
        type: String
    },
    methods: {
        getBgClass() {
            return `bg-${this.type.toLowerCase()}`;
        }
    }
}
</script>

<template>
    <div class="card" :class="getBgClass()">
        <img :src="image" :alt="name">
        <p>{{ number }}</p>
        <h4>{{ name }}</h4>
        <p><i>{{ type }}</i></p>
    </div>
</template>

<style lang="scss" scoped>
.card {
    border-radius: 15px;
    text-align: center;
    padding: 15px 0;
}

img {
    width: 150px;
    height: 150px;
    border-radius: 50%;
    object-fit: contain;
    background-color: white;
}

h4 {
    margin: 5px 0;
}
</style>