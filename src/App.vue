<template>
  <div class="ctr">
    <div class="Header">Quiz App</div>
    <transition name="fade" mode="out-in">
      <Questions
        v-if="questionsAnswered < questions.length"
        :questions="questions"
        :questionsAnswered="questionsAnswered"
        @question-answered="questionAnswered" />
      <Results v-else :results="results" :totalCorrect="totalCorrect" />
    </transition>

    <button
      type="button"
      class="reset-btn"
      @click.prevent="reset"
      v-if="this.questionsAnswered === questions.length">
      Reset
    </button>
  </div>
</template>
<script>
import Questions from './components/Questions.vue';
import Results from './components/Results.vue';
export default {
  name: 'App',
  components: {
    Questions,
    Results,
  },
  data() {
    return {
      questionsAnswered: 0,
      totalCorrect: 0,
      questions: [
        {
          q: 'Which planet is known as the "Red Planet"?',
          answers: [
            {
              text: 'Venus',
              is_correct: false,
            },
            {
              text: 'Mars',
              is_correct: true,
            },
            {
              text: 'Jupiter',
              is_correct: false,
            },
            {
              text: 'Saturn',
              is_correct: false,
            },
          ],
        },
        {
          q: 'Who painted the Mona Lisa?',
          answers: [
            {
              text: 'Vincent van Gogh',
              is_correct: false,
            },
            {
              text: 'Leonardo da Vinci',
              is_correct: true,
            },
            {
              text: ' Pablo Picasso',
              is_correct: false,
            },
            {
              text: 'Michelangelo',
              is_correct: false,
            },
          ],
        },
        {
          q: 'What is the chemical symbol for gold?',
          answers: [
            {
              text: 'Go',
              is_correct: false,
            },
            {
              text: 'Au',
              is_correct: true,
            },
            {
              text: 'Ag',
              is_correct: false,
            },
            {
              text: 'Pt',
              is_correct: false,
            },
          ],
        },
        {
          q: 'Who wrote the play "Romeo and Juliet"?',
          answers: [
            {
              text: 'William Shakespeare',
              is_correct: true,
            },
            {
              text: 'Oscar Wilde',
              is_correct: false,
            },
            {
              text: 'Jane Austen',
              is_correct: false,
            },
            {
              text: 'Charles Dickens',
              is_correct: false,
            },
          ],
        },
        {
          q: 'Which country is known for inventing the sport of cricket?',
          answers: [
            {
              text: 'England',
              is_correct: true,
            },
            {
              text: 'Australia',
              is_correct: false,
            },
            {
              text: 'India',
              is_correct: false,
            },
            {
              text: 'South Africa',
              is_correct: false,
            },
          ],
        },
        {
          q: 'What is the tallest mountain in the world?',
          answers: [
            {
              text: 'Mount Kilimanjaro',
              is_correct: false,
            },
            {
              text: 'Mount Everest',
              is_correct: true,
            },
            {
              text: 'Mount Fuji',
              is_correct: false,
            },
            {
              text: 'Mount McKinley',
              is_correct: false,
            },
          ],
        },
        {
          q: 'Which famous scientist developed the theory of relativity?',
          answers: [
            {
              text: ' Isaac Newton',
              is_correct: false,
            },
            {
              text: 'Albert Einstein',
              is_correct: true,
            },
            {
              text: 'Charles Darwin',
              is_correct: false,
            },
            {
              text: 'Nikola Tesla',
              is_correct: false,
            },
          ],
        },
        {
          q: 'Who painted the ceiling of the Sistine Chapel?',
          answers: [
            {
              text: 'Vincent van Gogh',
              is_correct: false,
            },
            {
              text: 'Leonardo da Vinci',
              is_correct: false,
            },
            {
              text: 'Michelangelo',
              is_correct: true,
            },
            {
              text: 'Pablo Picasso',
              is_correct: false,
            },
          ],
        },
        {
          q: 'What is the largest organ in the human body?',
          answers: [
            {
              text: 'Liver',
              is_correct: false,
            },
            {
              text: 'Brain',
              is_correct: false,
            },
            {
              text: 'Heart',
              is_correct: false,
            },
            {
              text: 'Skin',
              is_correct: true,
            },
          ],
        },
        {
          q: 'Which country is known as the "Land of the Rising Sun"?',
          answers: [
            {
              text: 'China',
              is_correct: false,
            },
            {
              text: 'Japan',
              is_correct: true,
            },
            {
              text: 'South Korea',
              is_correct: false,
            },
            {
              text: 'Norway',
              is_correct: false,
            },
          ],
        },
      ],
      results: [
        {
          min: 0,
          max: 5,
          title: 'Try again!',
          desc: 'Do a little more studying and you may succeed!',
        },
        {
          min: 8,
          max: 10,
          title: "Wow, you're a genius!",
          desc: 'Studying has definitely paid off for you!',
        },
      ],
    };
  },
  methods: {
    questionAnswered(is_correct) {
      if (is_correct) {
        this.totalCorrect++;
      }
      this.questionsAnswered++;
    },
    reset() {
      this.questionsAnswered = 0;
      this.totalCorrect = 0;
    },
  },
};
</script>
