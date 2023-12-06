<script>
import Block from './components/Block.vue'
import Results from './components/Results.vue'

  export default {
    name: 'App', 
    components: { 
      Block,
      Results
    },
    data() {
      return {
        isPlaying: false,
        dalay: null,
        score: null,
        showResults: false,
      }
    },
    methods: {
      start() {
        this.delay = 2000 + Math.random() * 5000
        this.isPlaying = true
        this.showResults = false
      },

      endGame(reactionTime) {
        this.score = reactionTime
        this.isPlaying = false
        this.showResults = true
      }
    } 
  }
</script>

<template>
  <div class="body">
    <h1>REACTION TIMER</h1>
    <button @click="start" class="start-btn" :disabled="isPlaying">PLAY</button>
    <Block v-if="isPlaying" :delay="delay" @end="endGame"/>
    <Results v-if="showResults" :score="score"/>
  </div>
</template>

<style>
  .body {
    display: flex;
    flex-direction: column;
  }

  h1 {
    padding: 50px;
    margin: 0 auto;
  }

  .start-btn {
    height: 40px;
    width: 400px;
    border: 1px solid #e983d9;
    border-radius: 10px;
    background-color: #fefefe;
    font-weight: 500;
    color: #302e2e;
  }
</style>
