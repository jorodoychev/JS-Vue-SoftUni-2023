<script>
export default {
  data() {
    return {
      isThinking: false,
      hasAnswer: false,
      answer: '',
      possibleAnswers: ['Yes', 'No', 'Maybe'],
      isRotating: false,
      isGreen: false,
      isRed: false,
    }
  },
  methods: {
    startThinking() {
      this.answer = ''
      this.hasAnswer = false
      this.isThinking = true
      this.isRotating = true
      this.isGreen = false
      this.isRed = false
      setTimeout(() => {
        this.isThinking = false
        this.isRotating = false
        this.hasAnswer = true
        this.answer = this.possibleAnswers[Math.floor(Math.random() * this.possibleAnswers.length)]
        this.isGreen = this.answer.includes('Yes')
        this.isRed = this.answer.includes('No')
      }, 2000)
    }
  }
}
</script>

<template>
  <div>
    <img
        src="https://th.bing.com/th/id/R.156fe9f82d70bc8cf4b112d62114470b?rik=x4EUHzSU4UfBWQ&riu=http%3a%2f%2fwww.pngmart.com%2ffiles%2f3%2f8-Ball-Pool-PNG-Photos.png&ehk=L8VtaZPWFSUFvcqSqx6DZcE%2fL2Wg3J5qUwilqlwVzCo%3d&risl=&pid=ImgRaw&r=0"
        alt="" width="200" :class="{rotate: isRotating}">
    <h3 v-if="isThinking">Thinking...</h3>
    <h3 v-if="hasAnswer" :class="{green: isGreen, red: isRed}">{{ answer }}</h3>
    <button @click="startThinking">Ask me some question!</button>
  </div>
</template>

<style scoped>
img {
  display: block;
  margin: auto;
  padding-top: 70px;
  padding-bottom: 50px;
}

h3 {
  font-size: 24px;
  text-align: center;
}

.green {
  color: green;
}

.red {
  color: red;
}

.rotate {
  animation: rotation 2s;
  animation-timing-function: linear;
  animation-iteration-count: infinite;
}

@keyframes rotation {
  from {
    transform: rotate(0deg);
  }
  to {
    transform: rotate(359deg);
  }
}

button {
  width: 100%;
  padding: 20px;
  color: white;
  font-size: 20px;
  border-radius: 20px;
  border: none;
  background-color: cornflowerblue;
  cursor: pointer;
}
</style>
