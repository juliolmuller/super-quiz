<template>
  <div id="app">
    <header id="app-header">
      <h1>Super Quiz</h1>
    </header>
    <div class="wrapper">
      <main id="app-main">
        <transition name="flip" mode="out-in">
          <Result :correct="isCorrect" @next="getNextQuestion" v-if="isResponded" />
          <Question :question="questions[currQuestion]" @response="displayResult" v-else />
        </transition>
      </main>
    </div>
    <footer id="app-footer">
      <span>Todos os direitors reservados &copy; 2020 LacusSoft</span>
    </footer>
  </div>
</template>

<script>
import Question from './components/Question.vue'
import Result from './components/Result.vue'
import data from './data.json'

export default {

  components: {
    Question,
    Result,
  },

  data: () => ({
    questions,
    currQuestion: 0,
    isCorrect: false,
    isResponded: false,
  }),

  methods: {
    displayResult(isCorrect) {
      this.isCorrect = isCorrect
      this.isResponded = true
    },
    getNextQuestion() {
      this.currQuestion = (this.currQuestion + 1) % this.questions.length
      this.isResponded = false
    },
  },
}
</script>

<style>
* {
  margin: 0;
  padding: 0;
  box-sizing: border-box;
  color: #FFF;
  font-family: 'Oswald', sans-serif;
}

body {
  background: linear-gradient(to right, rgb(0, 0, 70), rgb(28, 181, 224));
}

html, body, #app {
  height: 100%;
}

#app {
  display: flex;
  flex-direction: column;
  align-items: center;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
}

#app-header {
  flex-shrink: 0;
}

#app-header h1 {
  padding: 2rem;
  font-size: 4rem;
  font-weight: 200;
}

.wrapper {
  flex-grow: 1;
  display: flex;
  width: 100%;
}

#app-main {
  display: flex;
  flex-direction: column;
  align-items: center;
  width: 100%;
  max-width: 1280px;
  margin: 0 auto;
  padding: 2rem;
}

#app-footer {
  flex-shrink: 0;
}

#app-footer span {
  display: block;
  padding: 2rem;
  color: #aaa;
  font-size: small;
}

@keyframes flip-out {
  from { transform: rotateY(0deg); }
  to { transform: rotateY(90deg); }
}

@keyframes flip-in {
  from { transform: rotateY(90deg); }
  to { transform: rotateY(0deg); }
}

.flip-enter-active {
  animation: flip-in 0.3s ease;
}

.flip-leave-active {
  animation: flip-out 0.3s ease;
}
</style>
