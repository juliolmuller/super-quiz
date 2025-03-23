<script>
export default {
  name: 'Result',

  emits: ['next'],

  props: {
    correct: {
      type: Boolean,
      required: true,
    },
  },
};
</script>

<template>
  <div class="result" :class="{ wrong: !correct }">
    <div class="message">
      <p class="icon">{{ correct ? '✔' : '❌' }}</p>
      <p v-if="correct" class="text">Resposta correta!</p>
      <p v-else class="text">Resposta errada</p>
    </div>

    <button :class="{ wrong: !correct }" @click="$emit('next')">Próxima Pergunta &gt;</button>
  </div>
</template>

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
  background-color: #ed213a;
  background: linear-gradient(to top, #93291e, #ed213a);
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

.result button:hover,
.result button:focus {
  background-color: #ddd;
  cursor: pointer;
}

.result.wrong button {
  color: #93291e;
}
</style>
