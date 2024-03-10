<script>
export default {
  data: () => ({
    count: 10,
    counterTitle: 'Counter Standart',
    incrementAmount: 8,
    message: 'Hello it works',
    listOfNumbers: [
      { name: 1, id: '1', list: [1, 2, 3] },
      { name: 2, id: '2', list: [1, 2, 3] },
      { name: 3, id: '3', list: [1, 2, 3] },
      { name: 4, id: '4', list: [1, 2, 3] },
      { name: 5, id: '5', list: [1, 2, 3] }
    ]
  }),
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
    incrementCount(newAmount, event) {
      console.log(newAmount)
      console.log(event)
      this.count += this.optimizedIncrementAmount
    }
  },
  watch: {
    count(newValue) {
      console.log(newValue)
      if (newValue > 20) {
        this.counterTitle += ' Very Long'
      }
    }
  }
}
</script>

<template>
  <h1>{{ displayTitle }}</h1>
  <p :data-increment-by="incrementAmount">{{ count }}</p>
  <button @click="incrementCount(10, $event)">Increment Count</button>
  <h1>{{ incrementAmount }}</h1>
  <p>{{ optimizedIncrementAmount }}</p>
  <div>
    <label for="incrementAmount">Increment by:</label>
    <input type="number" v-model="incrementAmount" />
  </div>
  <hr />
  <p v-if="message.length % 2 === 0">Even:{{ message.toUpperCase() }}</p>
  <p v-else>Odd:{{ message }}</p>
  <ul v-for="(item, index) in listOfNumbers" :key="`item-${index}`">
    <li>
      {{ item.id }}
      <ul>
        <li v-for="(number, index) in item.list" :key="`number-${index}`">{{ number }}</li>
      </ul>
    </li>
  </ul>
</template>
