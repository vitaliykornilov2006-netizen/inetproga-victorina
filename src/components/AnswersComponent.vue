<template>
  <div class="answers-wrapper">
    <div class="answers">
      <img
        v-for="(img, index) in props.answers"
        :key="index"
        :src="img"
        :class="{
          correct: selected !== null && index === props.correct,
          incorrect: selected !== null && index === selected && selected !== props.correct,
        }"
        @click="selectAnswer(index)"
      />
    </div>

    <!-- кнопка -->
    <img
      src="/IMGWKI/34.png"
      class="next-btn"
      :class="{ visible: selected !== null }"
      @click="next"
    />
  </div>
</template>

<script setup lang="ts">
import { ref, watch } from 'vue'

const props = defineProps<{
  answers: string[]
  correct: number
}>()

// умеет  отправлять 2 события
const emit = defineEmits(['answered', 'next-question'])

// какой ответ выбрал
const selected = ref<number | null>(null)

function selectAnswer(index: number) {
  if (selected.value === null) {
    selected.value = index
    emit('answered', index === props.correct)
  }
}

function next() {
  if (selected.value !== null) {
    emit('next-question')
  }
}

// сброс при смене вопроса
watch(
  () => props.answers,
  () => {
    selected.value = null
  },
)
</script>

<style scoped>
.answers {
  display: flex;
  justify-content: center;
  gap: 53px;
}

.answers img {
  width: 200px;
  height: 257px;
  object-fit: contain;
  border-radius: 16px;
}

.answers img.correct {
  outline: 4px solid #00ff00;
  outline-offset: -4px;
}

.answers img.incorrect {
  outline: 4px solid #ff0000;
  outline-offset: -4px;
}

.next-btn {
  width: 82px;
  height: 82px;
  cursor: pointer;
  visibility: hidden;
}
.next-btn.visible {
  visibility: visible;
  opacity: 1;
}

.next-btn:hover {
  transform: scale(1.1);
}
</style>
