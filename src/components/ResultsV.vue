<template>
  <p class="scoreTitle">Your reaction time is: {{ score }}</p>
  <p class="rank">Your rank is: {{ rank }}</p>
</template>

<script>
export default {
  props: ["score"],
  data() {
    return {
      rank: null,
    };
  },
  mounted() {
    if (this.score < 350) {
      this.rank = "Godlike";
    } else if (this.score < 700) {
      this.rank = "Pro";
    } else if (this.score < 1200) {
      this.rank = "Average";
    } else {
      this.rank = "Noob";
    }
  },
};
</script>

<style>
.scoreTitle {
  color: rgb(11, 11, 11);
  font-size: 2em;
  font-weight: bold;
}

.rank {
  color: rgb(7, 7, 7);
  font-size: 4em;
  font-weight: bold;
}
</style>
