<script>
import BaseCounter from './components/BaseCounter.vue'
export default {
  components: {
    BaseCounter
  },
  data: () => ({
    message: 'Hello it works',
    listOfNumbers: [
      { name: 1, id: '1', list: [1, 2, 3] },
      { name: 2, id: '2', list: [1, 2, 3] },
      { name: 3, id: '3', list: [1, 2, 3] },
      { name: 4, id: '4', list: [1, 2, 3] },
      { name: 5, id: '5', list: [1, 2, 3] }
    ]
  })
}
</script>

<template>
  <BaseCounter />
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
./components/BaseCounter.vue
