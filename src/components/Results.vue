<template>
  <div>Reaction time: {{ score }} ms</div>
  <p class="rank">{{ rank }}</p>
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
      if (this.scrore < 250) {
        this.rank = 'Thunder speed!'
      } else if (this.rank < 400) {
        this.rank = 'Rapid reflexes!'
      } else {
        this.rank = 'snail pace...'
      }
    }
}
</script>

<style>
.rank {
  font-size: 24px;
  color: #0faf87;
  font-weight: bold;
  }
</style>