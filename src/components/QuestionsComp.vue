<template>
  <div class="questions-ctr">
    <div class="progress">
      <div class="bar"></div>
      <div class="status">1 out of 3 questions answered</div>
    </div>
    <div
      class="single-question"
      v-for="(question, qi) in questions"
      :key="question.q"
      v-show="qi == questionsAnswered"
    >
      <div class="question">{{ question.q }}</div>
      <div class="answers">
        <div
          class="answer"
          v-for="answer in question.answers"
          :key="answer.text"
          @click="selectAnswer(answer.is_correct)"
        >
          {{ answer.text }}
        </div>
      </div>
    </div>
  </div>
</template>

<script lang="ts">
import type { Question } from '@/static/data'
import { defineComponent, type PropType } from 'vue'
export default defineComponent({
  data() {
    return {}
  },
  props: {
    questions: {
      type: Object as PropType<Question[]>,
      required: true,
    },
    questionsAnswered: {
      type: Number,
      required: true,
    },
  },
  methods: {
    selectAnswer(isCorrect: boolean) {
      this.$emit('questionAnsweredEvent', isCorrect)
    },
  },
  emits: {
    // eslint-disable-next-line @typescript-eslint/no-unused-vars
    questionAnsweredEvent(isCorrect: boolean) {
      return true
    },
  },
})
</script>

<style scoped></style>
