<template>
  <div class="jumbotron text-center mt-3 bg bg-light p-5 col-4 ms-auto me-auto">
    <h3>{{ cQuestion.question }}</h3>
    <hr class="my-4" />
    <p v-for="(answer , i) in answers"  :key="i">{{ answer }}</p>
    <a class="btn btn-primary ms-sm-5 mb-3" href="#" role="button">submit</a>
    <a class="btn btn-success ms-sm-5 mb-3" href="#" role="button" @click="next"
      >next</a
    >
  </div>
</template>

<script>
export default {
  props: {
    cQuestion: Object,
    next: Function,
  },
  computed: {
    answers() {
      let answers = [...this.cQuestion.incorrect_answers];
      answers.push(this.cQuestion.correct_answer);
      return answers;
    },
  },
};
</script>

<style></style>
