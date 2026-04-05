<script setup lang="ts">
import { ref, computed } from 'vue'
import AnswersComponent from './components/AnswersComponent.vue'
import QuestionComponent from './components/QuestionComponent.vue'
import NavigationComponent from './components/NavigationComponent.vue'
import data from './components/data.json'

const currentIndex = ref(0)

// массив результатов (0 / тру / фальс)
const results = ref<(boolean | null)[]>(Array(data.length).fill(null))

const correctCount = computed(() => {
  return results.value.filter((r) => r === true).length
})

function handleAnswer(isCorrect: boolean) {
  results.value[currentIndex.value] = isCorrect
}

function nextQuestion() {
  if (currentIndex.value < data.length - 1) {
    currentIndex.value++
  } else {
    currentIndex.value++ //чтобы показать результат
  }
}
</script>

<template>
  <div class="zxc">
    <img src="/IMGWKI/cleft.png" class="bgd left" />
    <img src="/IMGWKI/cright.png" class="bgd right" />

    <div class="panel">
      <div class="innerPanel">
        <div class="dblinnerPanel">
          <template v-if="currentIndex < data.length">
            <!-- прогресссс -->
            <NavigationComponent :results="results" />

            <!-- вопросики -->
            <QuestionComponent :question="data[currentIndex]!.question" />

            <!-- ответики -->
            <div class="otvetiki">
              <AnswersComponent
                :answers="data[currentIndex]!.answers"
                :correct="data[currentIndex]!.correct"
                @answered="handleAnswer"
                @next-question="nextQuestion"
              />
            </div>
          </template>
          <template v-else>
            <div class="result">Количество правильных ответов: {{ correctCount }}</div>
          </template>
        </div>
      </div>
    </div>
  </div>
</template>

<style>
html,
body,
#app {
  margin: 0;
  padding: 0;
  height: 100%;
  background: #2e015c;
}

.zxc {
  width: 100vw;
  min-height: 100vh;
  display: flex;
  align-items: center;
  justify-content: center;
}

.panel {
  /* Rectangle 2.2 */

  position: relative;
  width: 1104px;
  height: 822px;
  box-sizing: border-box;

  background: linear-gradient(261.38deg, #0060d9 18.47%, #004193 93.48%);
  border-radius: 60px;

  display: flex;
  align-items: center;
  justify-content: center;
  flex-direction: column;
}

.innerPanel {
  /* Rectangle 2.3 */

  position: absolute;
  width: 1095px;
  height: 813px;
  left: 0px;
  top: 0px;

  background: linear-gradient(37.63deg, #2b62d5 5.17%, #15aaff 59.05%);
  border-radius: 51px;
}

.dblinnerPanel {
  /* Rectangle 2.9 */

  position: absolute;
  width: 1095px;
  height: 813px;
  left: 0px;
  top: 0px;

  background: linear-gradient(
    241.84deg,
    #003dce -3.61%,
    rgba(21, 170, 255, 0) 48.73%,
    rgba(20, 164, 252, 0.0598291) 48.74%,
    #003dce 95.39%
  );
  border-radius: 51px;

  display: flex;
  flex-direction: column;
}

.left {
  /* Group 6 */

  position: absolute;
  width: 467px;
  height: 569.85px;
  left: 136px;
  top: 362.13px;
}

.right {
  /* Group 5 */

  position: absolute;
  width: 455.98px;
  height: 495px;
  left: 1287px;
  top: 91px;
}

.otvetiki {
  display: flex;
  flex-direction: column;
  align-items: center;
  justify-content: space-between;
  margin-top: auto;
}

.result {
  margin: 0 auto;
  margin-top: 200px;

  font-family: 'PT Sans Caption', sans-serif;
  font-size: 44px;
  line-height: 40px;
  text-align: center;
  color: white;
  white-space: pre-line;
}
</style>
