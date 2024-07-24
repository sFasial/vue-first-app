<template>
  <!-- <img alt="Vue logo" src="./assets/logo.png">
  <HelloWorld msg="Welcome to Your Vue.js App"/> -->
  <!-- <friends-component :friendsAppVueComponent = "friends"
  :cars="cars"></friends-component> -->

  <new-friend-component @add-friend="AddFriends">

  </new-friend-component>
  <friends-component 
  :friendsAppVueComponent="friends" 
  v-for="car in cars" :key="car.id" :cars=car 
  :counter="counter"
  @counter-will-increase="IncreaseCounter">
  </friends-component>

</template>

<script>
// import HelloWorld from './components/HelloWorld.vue'
import FriendsComponent from './components/FriendsComponent.vue'
import NewFriendComponent from './components/NewFriendComponent.vue'

export default {
  name: 'App',
  components: {
    // HelloWorld
    FriendsComponent,
    NewFriendComponent
  },
  data() {
    return {
    counter: 1,
      friends: [{
        id: 1,
        name: 'App Component Sabrina',
        email: 'App Component sabrina@gmail.com',
        number: 'App Component 123456789'
      }],
      cars: [{
        id: 1,
        name: 'BMW'
      }, {
        id: 2,
        name: 'MERCEDES'
      }, {
        id: 3,
        name: 'JAGUAR'
      }
      ]
    }
  },
  methods: {
    AddFriends(eventData){
      alert("Reached")
      console.log('eventData', eventData);

      const maxId = this.friends.length > 0 ? Math.max(...this.friends.map(f => f.id)) : 0;

      console.log('maxId', maxId);

      this.friends.push({
        id: maxId + 1,
        name: eventData.name,
        email: eventData.email,
        number: eventData.contactNumber
      });

    },
    IncreaseCounter(eventData){
      console.log('eventData', eventData);
      this.counter = this.counter + eventData; 
    }
  }
}
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
