<script>
import BaseCounter from './components/BaseCounter.vue';
import UserCard from './components/user-card.vue';
export default {
  components: { BaseCounter, UserCard},
    data() {
        return {
          message: 'Hello it works!!',
          listOfNumbers: [
            { name: '1', id: Math.random(), list: [1, 2, 3]}, 
            { name: '2', id: Math.random(), list: [1, 2, 3]}, 
            { name: '3', id: Math.random(), list: [1, 2, 3]}, 
            { name: '4', id: Math.random(), list: [1, 2, 3]}, 
            { name: '5', id: Math.random(), list: [1, 2, 3]}
          ],
          userData: {
            name: 'Ben',
            preferredFramework: 'vue',
            favoriteFood: "sushi",
            favoriteNumbers: [8,10,12]
          }
        }
      },
  };
</script>

<template>
  <!-- <UserCard :user="userData"/> -->
  <UserCard :name="userData.name" :favoriteFood="userData.favoriteFood" />
    <hr />
    <!-- v-if & v-else  -->
    <p v-if="message.length % 2 === 0">Even {{ message.toUpperCase()}}</p>
    <p v-else>Odd {{ message}}</p>
    <!-- v-for loop -->
    <ul v-for="(item, index) in listOfNumbers" v-bind:key="`item-${index}`">
      <li>
        {{  item.id }}
        <ul>
          <li 
          v-for="number in listOfNumbers" 
          v-bind:key="`item-${index}`" >
          {{ number.name + " " + number.id + " " + number.list}}
        </li>
        </ul>
      </li>
    </ul>
    <hr />


</template>
