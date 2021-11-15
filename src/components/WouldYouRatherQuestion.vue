<template>
  <div class="hello">
    <h2>Please make your choice:</h2>

    <!-- The question itself -->
    <h3>{{ question }}</h3>

    <!-- The first choice the user is offered -->
    <input type="radio" v-model="choice" v-bind:value="answer1" v-on:change="choiceMade">
    <label>{{ answer1 }}</label>

    <!-- The second choice the user is offered -->
    <input type="radio" v-model="choice" v-bind:value="answer2" v-on:change="choiceMade">
    <label>{{ answer2 }}</label>
  </div>
</template>

<script>
// The props which are used by the parent component
export default {
  name: 'WouldYouRatherQuestion',
  emits: ['answer-changed'],
  props: {
    question: String,
    answer1: String,
    answer2: String
  },
  data() {
    return {
      choice: ''
    }
  },
  methods: {
    // Sends the payload response to the parent component
    choiceMade() {
      this.$emit('answer-changed', this.choice)
    }
  }
}
</script>

<!-- Style below is only for this component -->
<style scoped>
h3 {
  margin: 40px 0 0;
}
ul {
  list-style-type: none;
  padding: 0;
}
li {
  display: inline-block;
  margin: 0 10px;
}
a {
  color: #42b983;
}
</style>
