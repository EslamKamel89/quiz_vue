<template>
  <div class="ctr">
    <QuestionsComp v-if="questionsAnswered < questions.length" :questions="questions" />
    <ResultComp v-else />
    <button type="button" class="reset-btn">Reset</button>
  </div>
</template>

<script lang="ts">
import data from '@/static/data.ts'
import { defineComponent } from 'vue'
import QuestionsComp from './components/QuestionsComp.vue'
import ResultComp from './components/ResultComp.vue'
import { pr } from './pr'

export default defineComponent({
  name: 'App',
  data() {
    return {
      questions: [...data.questions],
      results: [...data.results],
      questionsAnswered: 0,
    }
  },
  components: {
    QuestionsComp,
    ResultComp,
  },
  mounted() {
    pr(this.questions.length, 'questions.length')
  },
})
</script>

<style scoped></style>
