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
    }, 
    emits: ['change-name'],
    methods: {
        tellParentToChangeName() {
            this.$emit('change-name')
        }
    }
}
</script>
<template>
    <h1>User: {{ user.name}}</h1>
    <p>Fav food: {{  user.favoriteFood}}</p>
    <!-- emit event -->
    <button @click="tellParentToChangeName">Change name</button>
    <!-- //new alternative  -->
    <!-- <button @click="$emit('change-name')">Change name</button> -->

</template>