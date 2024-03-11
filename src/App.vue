<script>
import BaseCounter from './components/BaseCounter.vue'
import UserCard from './components/UserCard.vue'

export default {
  components: {
    BaseCounter,
    UserCard
  },
  data: () => ({
    message: 'Hello it works',
    listOfNumbers: [
      { name: 1, id: '1', list: [1, 2, 3] },
      { name: 2, id: '2', list: [1, 2, 3] },
      { name: 3, id: '3', list: [1, 2, 3] },
      { name: 4, id: '4', list: [1, 2, 3] },
      { name: 5, id: '5', list: [1, 2, 3] }
    ],
    userData: {
      name: 'Ben',
      preferredFramework: 'vue',
      favoriteFood: 'sushi',
      favoriteNumbers: [8, 10, 12]
    }
  }),
  computed: {
    refinedUserData() {
      return {
        name: this.userData.name,
        food: this.userData.favoriteFood
      }
    }
  }
}
</script>

<template>
  <UserCard :user="refinedUserData" />
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
