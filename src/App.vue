<script setup>
import QuestionsSet from "@/components/QuestionsSet.vue";
import QuizResult from "@/components/QuizResult.vue";
import { ref } from "vue";

let questionsAnswered = ref(0);
let totalCorrect = ref(0);

const questionAnswered = (is_correct) => {
  if (is_correct) totalCorrect.value++;

  questionsAnswered.value++;
};

const reset = () => {
  questionsAnswered.value = 0;
  totalCorrect.value = 0;
};

const questions = [
  {
    q: "What is 2 + 2?",
    answers: [
      {
        text: "4",
        is_correct: true,
      },
      {
        text: "3",
        is_correct: false,
      },
      {
        text: "Fish",
        is_correct: false,
      },
      {
        text: "5",
        is_correct: false,
      },
    ],
  },
  {
    q: 'How many letters are in the word "Banana"?',
    answers: [
      {
        text: "5",
        is_correct: false,
      },
      {
        text: "7",
        is_correct: false,
      },
      {
        text: "6",
        is_correct: true,
      },
      {
        text: "12",
        is_correct: false,
      },
    ],
  },
  {
    q: "Find the missing letter: C_ke",
    answers: [
      {
        text: "e",
        is_correct: false,
      },
      {
        text: "a",
        is_correct: true,
      },
      {
        text: "i",
        is_correct: false,
      },
    ],
  },
];
const results = [
  {
    min: 0,
    max: 2,
    title: "Try again!",
    desc: "Do a little more studying and you may succeed!",
  },
  {
    min: 3,
    max: 3,
    title: "Wow, you're a genius!",
    desc: "Studying has definitely paid off for you!",
  },
];
</script>

<template>
  <div class="ctr">
    <transition name="fade" mode="out-in">
      <QuestionsSet
        v-if="questionsAnswered < questions.length"
        :questions="questions"
        :questions-answered="questionsAnswered"
        @question-answered="questionAnswered"
      />
      <QuizResult v-else :results="results" :total-correct="totalCorrect" />
    </transition>
    <button
      type="button"
      class="reset-btn"
      @click.prevent="reset"
      v-if="questionsAnswered === questions.length"
    >
      Reset
    </button>
  </div>
</template>

<style scoped></style>
