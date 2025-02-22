<template>
  <div class="result">
    <h2>You got sample result {{ totalCorrect }}!</h2>
    <div
      v-for="result in results"
      :key="result.title"
      v-show="totalCorrect >= result.min && totalCorrect <= result.max"
    >
      <div class="title">{{ result.title }}</div>
      <div class="desc">{{ result.desc }}</div>
    </div>
  </div>
</template>

<script lang="ts">
import type { Result } from '@/static/data'
import { defineComponent, type PropType } from 'vue'

export default defineComponent({
  data() {
    return {}
  },
  props: {
    questionsAnswered: {
      type: Number,
      required: true,
    },
    totalCorrect: {
      type: Number,
      required: true,
    },
    results: {
      type: Object as PropType<Result[]>,
      required: true,
    },
  },
})
</script>
