<script>
export default {
  data() {
            return {
              newCharacter: {
                name: '',
                element: []
              },
              message: 'Movies list characters',
              movies: [
                {name: 'Aang', element:['air', 'earth', 'water', 'fire']},
                {name: 'Zuko', element:['fire']},
                {name: 'Toph', element:['earth']},
                {name: 'Katara', element:['water']},
            ],
            favouriteList: [],
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
          methods: {
            addNewCharacter(event) {
              this.movies.push(this.newCharacter);
              this.newCharacter = '';
            },
            setFavourite(character, event) {
              console.log(character.name)
              if(!this.favouriteList.includes(character.name)) {
                this.favouriteList.push(character.name)
              }
            }
          }
}

</script>

<template>
     <div id="app">
    <h1>Statistics</h1>
    <ul> Reduce function: 
  {{ statsBendersList}}
    </ul>
    <ul>
      <li v-for="(stat, type) in statsBendersList" :key="`bender-${stat}-${type}`">{{ type }} : {{ stat}}</li>
    </ul>
    <h2>Characters</h2>
    <p v-if="movies.length === 0">There are no characters.</p>
    <ul v-else>
        <li v-for="(name, index) in movies" :key="`even-character-${index}`">
          {{name.name}}  
          <button @click="setFavourite(name)">
            Favorite
          </button>
        </li>
       
    </ul>
 <h2>Fav characters</h2>
 <ul v-if="favouriteList.length > 0">
  <li v-for="(character, index) in favouriteList" :key="`odd-character-${index}`">{{character }}</li>
</ul>
<p v-else>No fav characters yet</p>

<h2>New character</h2>
<pre>
  {{newCharacter}}
</pre>
<label for="character-name">Name</label>
<input type="text" id="character-name" v-model="newCharacter.name" @keyup.enter="addNewCharacter">



    <p><span v-for="(character, index) in movies" :key="`comma-list-character-${index}`">{{character.name}}
        {{index === movies.length - 1? '' : ", "}}
    </span></p>
    </div>
</template>

<style scoped>

</style>
