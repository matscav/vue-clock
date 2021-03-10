<template>
  <div class="page-container">
    <img src="https://upload.wikimedia.org/wikipedia/commons/9/95/Vue.js_Logo_2.svg" alt="Vue logo" class="logo">
    <div class="container">
      <div class="dark-box">
          <div class="hour">{{ hour }}</div>
          <div class="dots">:</div>
          <div class="min">{{ min }}</div>
          <div class="dots">:</div>
          <div class="sec">{{ sec }}</div>
          <div class="mode">{{ timeZone }}</div>
      </div>
      <p class="copyright">Creado por <strong class="author">{{ fullName }}</strong></p>
    </div>
  </div>
</template>

<script>
export default {
  name: 'App',
  data () {
    return {
      fullName: 'Mathias Scavello',
      hour: '--',
      min: '--',
      sec: '--',
      timeZone: ''
    };
  },
  methods: {
    setTime () {
      setInterval(() => {
        const actualDate = new Date();
        this.hour = actualDate.getHours().toString().padStart(2, '0');
        this.min = actualDate.getMinutes().toString().padStart(2, '0');
        this.sec = actualDate.getSeconds().toString().padStart(2, '0');
        this.timeZone = (actualDate.getHours() < 12) ? 'AM' : 'PM';
      }, 1000);
    }
  },
  mounted () {
    this.setTime();
  }
};
</script>

<style>
@import url('https://fonts.googleapis.com/css2?family=DotGothic16&display=swap');
@import url('https://fonts.googleapis.com/css2?family=Lato&display=swap');
body {
  margin: 0;
  display: flex;
  justify-content: center;
  align-items: center;
  height: 100vh;
}
.author {
  color: aquamarine;
}
.container {
  background: linear-gradient(to right, grey, rgb(46, 44, 44));
  width: 750px;
  height: 250px;
  display: flex;
  justify-content: space-evenly;
  flex-direction: column;
  align-items: center;
}
.dark-box {
  font-family: 'DotGothic16', sans-serif;
  font-weight: 500;
  width: 700px;
  height: 150px;
  background: black;
  border-radius: 20px;
  color: red;
  font-size: 80px;
  display: flex;
  justify-content: space-evenly;
  align-items: center;
  box-shadow: 0px 0px 15px #000;
}
.dots {
  animation: blink 2s linear infinite;
}
@keyframes blink {
  0%, 100% { opacity: 1.0; }
  50% { opacity: 0.0; }
}
.copyright {
  font-family: 'Lato', sans-serif;
  margin: 0;
}
.logo {
  position: absolute;
  width: 450px;
  transform: translateX(-350px) translateY(-75px);
  z-index: -1;
}
</style>
