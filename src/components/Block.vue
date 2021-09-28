<template>
  <div class="block" v-if="showBlock" @click="stopTimer">
      click me
  </div>
</template>

<script>
export default {
    name: 'Block',
    props: ['delay'],
    data() {
        return {
        showBlock: false,
        timer: null,
        reactionTime: 0
        }
    },
    methods: {
        startTimer() {
            this.timer = setInterval(() => {
                this.reactionTime += 10;
            },10)
        },
        stopTimer() {
            clearInterval(this.timer)
            this.$emit('end', this.reactionTime)
        }
    },
    mounted() {
        setTimeout(() => {
            this.showBlock = true
            this.startTimer()
        }, this.delay)
    },
    updated() {

    }
}

</script>

<style lang="scss" scoped>
    .block {
    width: 300px;
    height: 300px;
    background-color: rgb(0, 162, 255);
    cursor: pointer;
    display: flex;
    justify-content: center;
    align-items: center;
    margin-top: 30px;
    color: #000;
}
</style>
