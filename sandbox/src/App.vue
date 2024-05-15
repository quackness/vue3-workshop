<script>

</script>

<template>
  <div id="app">
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
    <ul>
      <li v-for="number in listOfNumbers">{{ number.name + " " + number.id }}</li>
    </ul>
    <hr />


  </div>
</template>
