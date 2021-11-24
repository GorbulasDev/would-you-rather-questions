<template>
<div id="app">
  <h1>Would You Rather?</h1>
  
  <!-- We are inside WouldYouRatherQuestion, thus using its props as values -->
  <!-- We are iterating over each question and displaying them accordingly, with their props and values -->
  <would-you-rather-question
    v-for="question in questions"
    v-bind:question="question.question"
    v-bind:key="question.id"
    v-bind:answer1="question.answer1"
    v-bind:answer2="question.answer2"
    v-on:answer-changed="answerChanged"
    v-bind:id="question.id">

  </would-you-rather-question>

  <h1>Would You Rather...</h1>
  <p>...? Try making a selection above</p>

  <!-- Placeholder that displays what the user selected as the option -->
  <div v-for="selectedChoice in selectedAnswers">
    <p>{{ selectedChoice }}</p>
  </div>

</div>
</template>

<script>
// Import the Child component into the main application.
import WouldYouRatherQuestion from './components/WouldYouRatherQuestion.vue'

export default {
  name: 'App',
  components: {
    WouldYouRatherQuestion
  },
  data() {
    return {
      // Questions to ask the user (3 total questions), with 2 choices offered.
      questions: [
      {
        id: 0,
        question: 'Would you rather be able to type/text very fast or be able to read really quickly?',
        answer1: 'Type/Text very fast',
        answer2: 'Read very quickly'
      },
      {
        id: 1,
        question: 'Would you rather be really good at math or really good at sports?',
        answer1: 'Math',
        answer2: 'Sports'
      },
      {
        id: 2,
        question: 'Would you rather be able to control fire or water?',
        answer1: 'Fire',
        answer2: 'Water'
      }],

      // Array to contain our stored values.
      selectedAnswers: []
    }
  },
  methods: {
    // Accept the Child's object payload.
    answerChanged(choice, id) {
      this.selectedAnswers[id] = choice
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
