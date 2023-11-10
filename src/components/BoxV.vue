<template>
  <div
    class="box-v"
    v-if="showBlock"
    @click="stopTimer"
    :style="{ 'margin-top': marginTop, 'margin-left': marginLeft }"
  >
    CLICK ME
  </div>
</template>

<script>
export default {
  props: ["delay"],
  data() {
    return {
      showBlock: false,
      timer: null,
      reactionTime: 0,
      marginTop: "0px",
      marginLeft: "0px",
    };
  },

  mounted() {
    this.generateRandomMargin();
    console.log("it is mounted");
    setTimeout(() => {
      this.showBlock = true;
      this.startTimer();
    }, this.delay);
  },
  methods: {
    startTimer() {
      this.timer = setInterval(() => {
        this.reactionTime += 10;
      }, 10);
    },
    stopTimer() {
      clearInterval(this.timer);
      this.$emit("stop", this.reactionTime);
    },
    generateRandomMargin() {
      this.marginTop =
        Math.floor(Math.random() * (window.innerHeight - 200)) + "px";
      console.log(this.marginTop);
      this.marginLeft =
        Math.floor(Math.random() * (window.innerWidth - 200)) + "px";
    },
  },

  updated() {
    console.log("it is updated");
  },
  unmounted() {
    console.log("it is unmounted");
  },
};
</script>

<style>
.box-v {
  width: 250px;
  height: 250px;
  line-height: 250px;
  border-radius: 20px;
  font-size: 2rem;
  font-weight: bold;

  background-image: url("../assets/download.jpeg");
  color: white;
  text-align: center;

  cursor: pointer;
  position: absolute;
}
</style>
