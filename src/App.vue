<template>
  <div id="app">
    <img id="image" src="./assets/logo.png" @click="start" :style="imgStyle" />
    <audio id="se" :src="seSoruce" ></audio>
  </div>
</template>

<script>

export default {
  data() {
    return {
      isDragging: false,
      position: 0,
      seSoruce: "./nc102252.wav"
    };
  },
  computed: {
    imgStyle() {
      return {
        right: this.position + "px",
      };
    },
  },
  methods: {
    start: () => {
      document.getElementById('se').play()
    }
  },
  mounted() {
    document.getElementById('se').addEventListener("ended", () => {
      const x = 10;
      if (this.isDragging) {
        this.position -= x;
      } else {
        this.position += x;
      }
      document.getElementById("se").play()
    })
    document.addEventListener("mousedown", () => {
      this.isDragging = true;
    });
    document.addEventListener("mouseup", () => {
      this.isDragging = false;
    });
  },
};
</script>


<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}

#image {
  position: absolute;
  right: 0;
  top: 0;
}
</style>
