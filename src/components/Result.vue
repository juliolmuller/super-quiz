<template>
  <div class="result" :class="{ wrong: !correct }">
    <div class="message">
      <p class="icon">{{ correct ? '✔' : '❌' }}</p>
      <p class="text" v-if="correct"> Resposta correta!</p>
      <p class="text" v-else>Resposta errada</p>
    </div>

    <button :class="{ wrong: !correct }" @click="$emit('next')">
      Próxima Pergunta &gt;
    </button>
  </div>
</template>

<script>
export default {
  name: 'Result',

  props: {
    correct: {
      type: Boolean,
      required: true,
    },
  },
}
</script>

<style scoped>
.result {
  display: flex;
  flex-direction: column;
  justify-content: space-around;
  height: 550px;
  width: 100%;
  max-width: 640px;
  width: 70%;
  border-radius: 20px;
  background-color: #118b11;
  background-image: linear-gradient(to bottom, #065506, #118b11);
  font-size: 5.5rem;
}

.result.wrong {
  background-color: #ED213A;
  background: linear-gradient(to top, #93291E, #ED213A);
}

.result button {
  align-self: center;
  outline: none;
  border: 0;
  border-radius: 8px;
  background-color: #fff;
  padding: 10px 20px;
  color: #065506;
  font-size: 1.7rem;
  font-weight: 600;
}

.result button:hover, .result button:focus {
  background-color: #ddd;
  cursor: pointer;
}

.result.wrong button {
  color: #93291E;
}
</style>
