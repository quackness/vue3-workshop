<script>
export default {
    props: {
        // text:String,
        // icon: String,
        left: Boolean,
        default: false
    }
}
</script>
<template>
    <!-- <button> {{  icon }} - {{  text }}</button> -->
    <button>
        <slot v-if="left">Icon -left</slot>
        <slot v-else>Submit</slot>
    </button>
</template>
