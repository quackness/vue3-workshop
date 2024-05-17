<script>
export default {
    props: {
        // user: {
        //     type: Object,
        //     required: true
        // }
        name: {
            type: String,
            default: "John Doe",
        },
        favoriteFood: {
            type: String,
            default: "Pizza"
        }
    }
}
</script>
<template>
    <h1>User: {{ name }}</h1>
    <p>Fav food: {{  favoriteFood }}</p>
</template>