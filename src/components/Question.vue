<template>
  <div ref="card" class="question">
    <span>{{ question.text }}</span>
    <div class="answers">
      <div
        class="answer"
        v-for="(answer, index) in question.answers"
        :key="index"
        @click="$emit('response', answer.correct)"
      >
        <span class="alternative">{{ alternatives[index] }}</span>
        <span class="text">{{ answer.text }}</span>
      </div>
    </div>
  </div>
</template>

<script>
import { ref } from 'vue'

export default {

  props: {
    question: {
      type: Object,
      required: true,
    },
  },

  setup: () => ({
    alternatives: ref([...'abcdefghij']),
  }),
}
</script>

<style scoped>
.question {
  min-height: 550px;
  width: 100%;
  max-width: 640px;
  padding: 1rem;
  border-radius: 20px;
  background-color: #fff;
  color: #000;
  font-size: 2.5rem;
}

.question > span {
  display: block;
  margin: 1rem 2rem 2rem;
  color: black;
}

.answers {
  display: flex;
  flex-direction: column;
  justify-content: center;
}

.answer {
  flex-basis: 90%;
  display: flex;
  margin: 0 1rem 2rem;
  border-radius: 8px;
  background: #396afc;
  background: linear-gradient(to right, #517cfd, #2948ff);
  font-size: 2rem;
}

.answer:hover, .answer:focus {
  background: darkblue;
  cursor: pointer;
}

.answers .alternative {
  flex-basis: 30px;
  padding: 10px;
  border-top-left-radius: 8px;
  border-bottom-left-radius: 8px;
  background-color: rgb(0, 0, 73);
  color: #fff;
  text-transform: uppercase;
}

.answers .text {
  flex-grow: 1;
  align-self: center;
  text-transform: uppercase;
}
</style>
