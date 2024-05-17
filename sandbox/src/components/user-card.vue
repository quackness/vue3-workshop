<script>
export default {
    props: {
        // user: {
        //     type: Object,
        //     required: true
        // }
        // name: {
        //     type: String,
        //     default: "John Doe",
        // },
        // favoriteFood: {
        //     type: String,
        //     default: "Pizza"
        // }
        user: {
            type: Object,
            required: true
        }
    }
}
</script>
<template>
    <h1>User: {{ user.name}}</h1>
    <p>Fav food: {{  user.favoriteFood}}</p>
</template>