<template>
  <div class="results">
    <p>Reaction time: {{ result }} ms</p>
    <p class="rank">{{ this.rank }}</p>
  </div>
</template>

<script>
export default {
  props: ['result'],
  data() {
    return {
      rank: null,
    }
  },
  mounted() {
    if (this.result < 250) {
      this.rank = 'Ninja fingers'
      console.log(this.rank)
    } else if (this.result < 450) {
      this.rank = 'Rapid Reflexes'
      console.log(this.rank)
    } else {
      this.rank = "You're a Snail"
      console.log(this.rank)
    }
  },
}
</script>

<style>
.results {
  margin: 2em auto;
}
.rank {
  font-size: 1.4em;
  color: #0faf87;
  font-weight: bold;
}
</style>
