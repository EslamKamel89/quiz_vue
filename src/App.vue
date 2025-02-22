<template>
  <div class="ctr">
    <QuestionsComp
      v-if="questionsAnswered < questions.length"
      :questions
      :questions-answered="questionsAnswered"
      @question-answered-event="handleQuestionAnswered"
    />
    <ResultComp v-else :questionsAnswered :totalCorrect :results />
    <button type="button" class="reset-btn" @click="reset">Reset</button>
  </div>
</template>

<script lang="ts">
import data from '@/static/data.ts'
import { defineComponent } from 'vue'
import QuestionsComp from './components/QuestionsComp.vue'
import ResultComp from './components/ResultComp.vue'

export default defineComponent({
  name: 'App',
  data() {
    return {
      questions: [...data.questions],
      results: [...data.results],
      questionsAnswered: 0,
      totalCorrect: 0,
    }
  },
  components: {
    QuestionsComp,
    ResultComp,
  },
  methods: {
    handleQuestionAnswered(isCorrect: boolean) {
      this.questionsAnswered++
      if (isCorrect) this.totalCorrect++
    },
    reset() {
      this.questionsAnswered = 0
      this.totalCorrect = 0
    },
  },
})
</script>

<style scoped></style>
