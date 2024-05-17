<script>
export default {
    //register props as options, can be done as an array
    // props: ['movies'],
    props: {
        movies: {
            type: Array,
        required: true
        }
     
    },
    computed: {
           statsBendersList() {
            const elements = ['air', 'earth', 'water', 'fire'];
            const statistics = {
              air: 0,
              earth: 0,
              water: 0,
              fire: 0
            };

            this.movies.forEach(character => {
              elements.forEach(element => {
                if (character.element.indexOf(element) > -1) {
                  statistics[element] += 1;
                }
            })
          })
              return statistics;
          }
        },
}
</script>
<template>
       <h1>Statistics</h1>
    <ul> Reduce function: 
  {{ statsBendersList}}
    </ul>
    <ul>
      <li v-for="(stat, type) in statsBendersList" :key="`bender-${stat}-${type}`">{{ type }} : {{ stat}}</li>
    </ul>
</template>