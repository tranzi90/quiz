<template>
  <div class="result">
    <div class="title">{{ results[resultIndex].title }}</div>
    <div class="desc">{{ results[resultIndex].desc }}</div>
  </div>
</template>

<script setup>
import { computed } from "vue";

const props = defineProps({
  results: Array,
  totalCorrect: Number,
});

const resultIndex = computed(() => {
  let ind = 0;
  props.results.forEach((el, i) => {
    if (props.totalCorrect < 3) return i;
    else ind = i;
  });
  return ind;
});
</script>

<style scoped></style>
