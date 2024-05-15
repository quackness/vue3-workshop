<script>
export default {
    data() {
        return {
          counterTitle: 'Counter Standard',
          message: 'Hello it works!!',
          listOfNumbers: [
            { name: '1', id: Math.random(), list: [1, 2, 3]}, 
            { name: '2', id: Math.random(), list: [1, 2, 3]}, 
            { name: '3', id: Math.random(), list: [1, 2, 3]}, 
            { name: '4', id: Math.random(), list: [1, 2, 3]}, 
            { name: '5', id: Math.random(), list: [1, 2, 3]}
          ],
          count: 10,
          incrementAmount: 8,

        }
      },
      computed: {
        displayTitle() {
          if (this.count > 20) {
            return 'Counter Standard - Very Long'
          } else {
            return 'Counter Standard'
          }
        },
        optimizedIncrementAmount() {
          return this.displayTitle.length * this.incrementAmount
        }
      },
      methods: {
        incrementCount() {
          this.count += this.optimizedIncrementAmount;
        }
      },
      watch: {
        count(newValue) {
          console.log(newValue)
        }

      }
  };
</script>

<template>

    <h1>{{ displayTitle }}</h1>
    <p :data-increment-by="incrementAmount">{{ count }}</p>
    <button @click="incrementCount">Increment count</button>
    <h1>{{ incrementAmount }}</h1>
    <p>{{ optimizedIncrementAmount }}</p>
    <div>
      <label for="incrementAmount">Increment by: </label>
      <input type="number" v-model="incrementAmount">
      </input>
    </div>
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
