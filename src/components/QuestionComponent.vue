<template>
  <div class="question">
    {{ question }}
  </div>
</template>

<script setup lang="ts">
defineProps<{
  question: string
}>()
</script>

<style scoped>
.question {
  max-width: 589px;
  margin: 0 auto;
  margin-top: 84px;

  font-family: 'PT Sans Caption', sans-serif;
  font-size: 22px;
  line-height: 40px;

  text-align: center;
  color: white;
  white-space: pre-line;
}
</style>
