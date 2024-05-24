<script>
export default {
    props: {
        name: {
            type: Object,
            required: true
        }
    },
    emits: ['favorite'],
    methods: {
    setFavourite() {
            //   console.log("test", name)
            //   if(!this.favouriteList.includes(character.name)) {
                // this.favouriteList.push(character.name)
                this.$emit('favorite', this.name)
            //   }
            }
        }
}
</script>
<template>
    <div>
        <p>{{name.name}}</p>
    <!-- click happens -->
          <button @click="setFavourite">Favorite</button>
    </div>
    
</template>

