<script>
import BaseCounter from './components/BaseCounter.vue';
import UserCard from './components/user-card.vue';
import BaseButton from './components/BaseButton.vue';
import BaseLayout from './components/BaseLayout.vue';


export default {
  components: { BaseCounter, UserCard, BaseButton, BaseLayout},
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
      computed: {
        refinedUserData() {
          return {
            name: this.userData.name,
            favoriteFood: this.userData.favoriteFood,
          }
        }
      },
      methods: {
        changeName() {
          this.userData.name = 'Charlie';
        }
      }
  };
</script>

<template>
  <!-- <UserCard :user="userData"/> -->
  <!-- <UserCard :name="userData.name" :favoriteFood="userData.favoriteFood" /> -->
  <!-- listen for the event to happen -->
  <!-- <BaseButton>Arrow Left - Hi</BaseButton> -->
  <!-- <BaseButton>{{ userData.name }}</BaseButton> -->
  <BaseLayout>
    <template v-slot:sidebar> This is aside block from BaseLayout</template>
    <template v-slot:main>   <UserCard :user="refinedUserData" @change-name="changeName"/></template>
    <template v-slot:footer> This is footer block from BaseLayout</template>
  </BaseLayout>
  <BaseButton :left="true"></BaseButton>

  <button @click="changeName">Change now</button>
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
