<template>
<div id="app">
  <h1>Would You Rather?</h1>
  
  <!-- We are inside WouldYouRatherQuestion, thus using its props as values -->
  <!-- We are iterating over each question and displaying them accordingly, with their props and values -->
  <would-you-rather-question
    v-for="wyrQuestion in questions"
    v-bind:question="wyrQuestion"
    v-bind:answer1="answer1"
    v-bind:answer2="answer2"
    v-on:answer-changed="answerChanged">
  </would-you-rather-question>
  
  <!-- Placeholder that displays what the user selected as the option -->
  <p>{{ userSelectionMessage }}</p>
</div>
</template>

<script>
// Import the Child component into the main application
import WouldYouRatherQuestion from './components/WouldYouRatherQuestion.vue'

export default {
  name: 'App',
  components: {
    WouldYouRatherQuestion
  },
  // Questions to ask the user (3 total questions), with 2 choices
  data() {
    return {
      questions: [
      // First question, with choices offered
      {
        id: 0,
        question: 'Would you rather be able to type/text very fast or be able to read really quickly?',
        answer1: 'Type/Text very fast',
        answer1: 'Read very quickly',
      },
      // Second question, with choices offered
      {
        id: 1,
        question: 'Would you rather be really good at math or really good at sports?',
        answer1: 'Math',
        answer1: 'Sports',
      },
      // Third question, with choices offered
      {
        id: 2,
        question: 'Would you rather be able to control fire or water?',
        answer1: 'Fire',
        answer1: 'Water',
      }]
    }
  },
  methods: {
    // Accept the Child's object payload
    answerChanged(choice) {
      this.userSelectionMessage = `Thanks! You chose ${choice}!`
    }
  }
}
</script>

<!-- The style is applied globally to the app -->
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
