<template>
  <div ref="main">
    <div ref="block" class="block" v-if="showBlock" @click="stopTimer">
      Click Me
    </div>
  </div>
</template>

<script>
export default {
  props: ['delay'],

  data() {
    return {
      showBlock: false,
      timer: null,
      reactionTime: 0
    }
  }, 

  mounted() {
    setTimeout(() => {
      this.showBlock = true;
      this.$nextTick(() => {
        this.positionBlock();
        this.startTimer();
      });
    }, this.delay);
  },

  methods: {
    positionBlock() {
      const box = this.$refs.block;
      const main = this.$refs.main;

      if (box && main) {
        box.style.right = Math.random() * 1000 + 'px';
        box.style.bottom = Math.random() * 1000 + 'px';
      }
    },
    startTimer() {
      this.timer = setInterval(() => {
        this.reactionTime += 10;
      }, 10);
    },
    stopTimer() {
      clearInterval(this.timer);
      this.$emit('end', this.reactionTime);
    }
  }
}
</script>

<style>
  .block {
    background-color: palevioletred;
    color: white;
    border: 1px solid transparent;
    border-radius: 10px;
    height: 150px;
    width: 400px;
    text-align: center;
    margin-top: 50px;
    padding: 50px;
    position: absolute;
    cursor: pointer;
  }
</style>
