<template>
  <div class="question-box-container">
    <b-jumbotron>
      <template slot="lead">{{ currentQuestion.question }}</template>
      <hr class="my-4" />
      <b-list-group>
        <b-list-group-item
          v-for="(answer,index) in answers"
          :key="index"
          @click="selectAnswer(index)"
        >{{ answer }}</b-list-group-item>
      </b-list-group>
      <b-button variant="primary" href="#">Submit</b-button>
      <b-button @click="next" variant="success" href="#">Next</b-button>
    </b-jumbotron>
  </div>
</template>
<script>
export default {
  props: {
    currentQuestion: Object,
    next: Function
  },
  data() {
    return {
      selectedIndex: null
    };
  },
  computed: {
    answers() {
      let answers = [...this.currentQuestion.incorrect_answers];
      answers.push(this.currentQuestion.correct_answer);
      return answers;
    }
  },
  methods: {
    selectAnswer(index) {
      this.selectedIndex = index;
      console.log(index);
    }
  }
};
</script>
<style scoped>
.btn {
  margin: 0 0.5rem;
}
.list-group {
  margin-bottom: 1rem;
}
.list-group-item:hover {
  background: #eee;
  cursor: pointer;
}
.selected {
  background-color: blue;
}
.correct {
  background-color: green;
}
.incorrect {
  background-color: red;
}
</style>