<template>
  <div class="result">
    <div class="title">{{ results[resultIndex].title }}</div>
    <div class="desc">{{ results[resultIndex].desc }}</div>
    <div class="total-correct">
      You have answered {{ totalCorrect }} out of 10 questions
    </div>
  </div>
</template>

<script>
export default {
  props: ['results', 'totalCorrect'],
  computed: {
    resultIndex() {
      let index = 0;
      this.results.forEach((e, i) => {
        if (e.min <= this.totalCorrect && e.max >= this.totalCorrect) {
          index = i;
        }
      });
      return index;
    },
  },
};
</script>

<style></style>
