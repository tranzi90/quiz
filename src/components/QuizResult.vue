<template>
  <div class="result">
    <div class="title">You got sample result 1!</div>
    <div class="desc">Enter a short description here about the result.</div>
  </div>
</template>

<script setup>
import { computed } from "vue";

const props = defineProps({
  results: Array,
  totalCorrect: Number,
});

const resultIndex = computed(() => {
  props.results.forEach((el, i) => {
    if (props.totalCorrect < 3) return i;
  });
  return props.results.length - 1;
});
</script>

<style scoped></style>
