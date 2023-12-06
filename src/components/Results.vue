<template>
  <p class="result">Reaction Time: {{ score }} ms - {{ rank }}</p>
</template>

<script>
export default {
  props: ['score'],
  data() {
    return {
      rank: null
    }
  },
  mounted() {
    if(this.score < 250) {
      this.rank = 'Ninja Fingers'
    } else if(this.score < 400) {
      this.rank = 'Rapid Reflexes'
    } else {
      this.rank = 'Loser!'
    }
  }
}
</script>

<style>
.result {
  margin-top: 20px;
  font-weight: 500;
  font-size: 24px;
  padding: 15px;
  border: 1px solid transparent;
  border-radius: 8px;
  background-color: pink;
  color: white;
}
</style>