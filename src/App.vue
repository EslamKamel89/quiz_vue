<template>
  <div class="ctr">
    <QuestionsComp />
    <ResultComp />
    <button type="button" class="reset-btn">Reset</button>
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
      data: { ...data },
    }
  },
  components: {
    QuestionsComp,
    ResultComp,
  },
})
</script>

<style scoped></style>
