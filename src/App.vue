<template>
  <h1>Raction Timer App</h1>
  <button @click="start" :disabled="isPlaying">Play</button>

    <!-- "end" ist Custom Event aus Block-Component; ":delay" und ":score" sind props -->
  <Block v-if="isPlaying" :delay="delay" @end="endGame" />

  <Result v-if="showResults" :score="score"/>
</template>



<script>
import Block from "./components/Block.vue"
import Result from "./components/Results.vue"

export default {
  name: 'App',
  components: { Block, Result },  
  data() {
    return {
      isPlaying: false,
      delay: null,
      showResults: false,
      score: null
    }
  },
  methods: {
    start() {
      // 2000 = 2000ms = 2sek; Math.random = 0 bis 1 
      // Umwandlung der Zahlenwerte in ms-Einheiten über JS-Funktion "setTimeout" in Block-Component
      this.delay = 2000 + Math.random() * 5000
      console.log(this.delay)
      
      this.isPlaying = true
      this.showResults = false
    },
    //"reactionTime" ist Value für endGame (kann auch anders definiert werden), kommt als reactionTime aus Block-Comp.
    endGame(reactionTime) {
      this.score = reactionTime
      this.isPlaying = false
      this.showResults = true
    }
  }
}
</script>




<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #444;
  margin-top: 60px;
}

button {
  background: #0faf87;
  color: white;
  font-size: 16px;
  letter-spacing: 1px;
  border-radius: 10px;
  padding: 8px 16px;
  margin: 10px;
  cursor: pointer;
}

button[disabled] {
  opacity: 0.2;
  cursor: not-allowed;
}
</style>
