<template>
<div id="app">
  <h1>Would You Rather?</h1>
  
  <!-- We are inside WouldYouRather, thus using its props as values. -->
  <would-you-rather
    v-bind:question="wyrQuestion"
    v-bind:answer1="wyrAnswer1"
    v-bind:answer2="wyrAnswer2"
    v-on:answer-changed="answerChanged">
  </would-you-rather>
  
  <p>{{ userSelectionMessage }}</p>
</div>
</template>

<script>
import WouldYouRather from './components/WouldYouRather.vue'

export default {
  name: 'App',
  components: {
    WouldYouRather
  },
  data() {
    return {
      wyrQuestion: 'Would you rather live in a house shaped like a circle or a triangle?',
      wyrAnswer1: 'Triangle House',
      wyrAnswer2: 'Circle House',
      userSelectionMessage: ''
    }
  },
  methods: {
    answerChanged(choice) {
      this.userSelectionMessage = `Thanks! You chose ${choice}!`
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
