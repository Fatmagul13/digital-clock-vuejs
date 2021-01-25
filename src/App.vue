<template>
  <div class="col-md-4 col-md-offset-4" id="clock">
    <h1>Digital Clock with Vue.js</h1>
    <p id="time">{{ time }}</p>

    <p id="date">{{ date }}</p>
  </div>
</template>

<script>
export default {
  name: "App",
  data() {
    return {
      time: "",
      date: "",
    };
  },
  methods: {
    zeroPadding(num, digit) {
      var zero = "";
      for (var i = 0; i < digit; i++) {
        zero += "0";
      }
      return (zero + num).slice(-digit);
    },
    updateTime() {
      var week = ["SUN", "MON", "TUE", "WED", "THU", "FRİ", "SAT"];
      var date = new Date();
      this.time =
        this.zeroPadding(date.getHours(), 2) +
        ":" +
        this.zeroPadding(date.getMinutes(), 2) +
        ":" +
        this.zeroPadding(date.getSeconds(), 2);
      this.date =
        this.zeroPadding(date.getFullYear(), 4) +
        "-" +
        this.zeroPadding(date.getMonth() + 1, 2) +
        "-" +
        this.zeroPadding(date.getDate(), 2) +
        " " +
        week[date.getDay()];
    },
  },
  mounted() {
    setInterval(() => {
      this.updateTime();
      console.log("timeout");
    }, 1000);
  },
};
</script>

<style>
#app {
  font-family: "Share Tech Mono", monospace;
}
body {
  background-color:#17202A;
  color: #fff;
}
#clock {
  position: absolute;
  top: 50%;
  left: 50%;
  transform: translateX(-50%) translateY(-50%);
  color: #D5D8DC;
  letter-spacing: 7px;
  text-align: center;
}
#time {
  font-size: 50px;
}
#date {
  font-size: 20px;
}
</style>
