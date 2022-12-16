<template>
  <p>Reaction time - {{ score }} ms</p>
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
        if (this.score < 250) {
            this.rank = 'Super Fingers'
        } else if (this.score <800) {
            this.rank = 'Rapid Reflexes'
        } else {
            this.rank = 'Snail'
        }
    }
}
</script>

<style>
.rank {
    font-size: 1.5em;
    color: coral;
    font-weight: bold;
}

</style>