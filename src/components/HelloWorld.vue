<template>
  <div class="hello">
    <div class="box" :class="{ red: isRed }"></div>
    <div class="box" :class="{ yellow: isYellow }"></div>
    <div class="box" :class="{ green: isGreen }"></div>
    <div class="box number">{{total}}</div>
  </div>
</template>

<script>
export default {
  name: 'HelloWorld',
  mounted() {
    this.countdown()
  },
  data() {
    return {
      total: 10,
      isRed: true,
      isYellow: false,
      isGreen: false,
    }
  },
  methods: {
    countdown() {
      let that = this
      redCtrl()

      function redCtrl() {
        if (that.total === 0) {
          that.total = 10
          that.isRed = !that.isRed
        }
        let timeIdRed = setInterval(function () {
          that.total--
          if (that.total <= 4) {
            that.isRed = !that.isRed
          }
          if (that.total === 0) {
            clearInterval(timeIdRed)
            yellowCtrl()
          }
        }, 1000)
      }

      function yellowCtrl() {
        that.isRed = false
        that.isYellow = !that.isYellow
        that.total = 5
        let timeIdYellow = setInterval(function () {
          that.total--
          if (that.total <= 3) {
            that.isYellow = !that.isYellow
          }
          if (that.total === 0) {
            clearInterval(timeIdYellow)
            greenCtrl()
          }
        }, 1000)
      }


      function greenCtrl() {
        that.isYellow = false
        that.isGreen = !that.isGreen
        that.total = 10
        let timeIdGreen = setInterval(function () {
          that.total--
          if (that.total <= 4) {
            that.isGreen = !that.isGreen
          }
          if (that.total === 0) {
            clearInterval(timeIdGreen)
            redCtrl()
          }
        }, 1000)
      }
    }
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
.hello {
  display: flex;
  justify-content: space-between;
  box-sizing: border-box;
  padding: 20px;
  width: 1200px;
  height: 300px;
  background-color: skyblue;
}

.box {
  width: 23%;
  height: 100%;
  background-color: #fff;
  border-radius: 50%;
}

.hello  div:last-child {
  border-radius: 0;
}

.red {
  background-color: red;
}

.yellow {
  background-color: yellow;
}

.green {
  background-color: green;
}

.number {
  display: flex;
  justify-content: center;
  align-items: center;
  font-size: 100px;
}
</style>
