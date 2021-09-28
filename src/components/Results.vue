<template>
  <div class="results">
      <p>Your score is: {{score}}</p>
      <p>Your score is: {{rank}}</p>
  </div>

</template>

<script>
export default {
    name: 'Results',
    props: ['score'],
    data() {
        return {
            rank: null
        }
    },
    mounted() {
        if(this.score < 250) {
            this.rank = 'Ninja'
        } else if(this.score < 400 ) {
            this.rank = 'Rapid'
        } else {
            this.rank = 'Snail pace'
        }
    }

}
</script>

<style>
.results {
    width: 200px;
    height: 200px;
    background-color: rgb(80, 0, 209);
    color: white;
    display: flex;
    justify-content: center;
    align-items: center;
    flex-direction: column;
    border-radius: 20px;
    margin-top: 20px}

</style>