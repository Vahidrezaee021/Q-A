<template>
  <Header :index="this.index" />
  <Content
    v-if="questionList.length"
    :cQuestion="questionList[index]"
    :next="next"
  />
</template>

<script>
import Header from "./components/Header.vue";
import Content from "./components/Content.vue";

export default {
  name: "App",
  components: {
    Header,
    Content,
  },
  data() {
    return {
      questionList: [],
      index: 0,
    };
  },
  methods: {
    next() {
      if (this.index < 19) {
        this.index++;
      }
    },
  },
  mounted: function () {
    fetch("https://opentdb.com/api.php?amount=20&category=11&type=multiple", {
      method: "get",
    })
      .then((response) => {
        return response.json();
      })
      .then((result) => {
        this.questionList = result.results;
        console.log(result.results);
      });
  },
};
</script>

<style></style>
