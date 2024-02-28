<template>
    <div>
      <h3>{{ question.text }}</h3>
      <ul>
        <li v-for="answer in question.answers" :key="answer.id">
          <input type="radio" v-model="selectedAnswer" :value="answer.id" />
          {{ answer.text }}
        </li>
      </ul>
    </div>
  </template>
  
  <script>
  export default {
    name: "Question",
    props: {
      question: {
        type: Object,
        required: true
      }
    },
    data() {
      return {
        selectedAnswer: null
      };
    },
    watch: {
      selectedAnswer(value) {
        this.$emit("answer-selected", value);
      }
    }
  };
  </script>