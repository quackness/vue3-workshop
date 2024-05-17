<script>
import BendersStats from './components/BendersStats.vue';
export default {
  components: { BendersStats },
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
 <BendersStats :movies="movies"/>
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
