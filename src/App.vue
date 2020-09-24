<template lang="pug">
  #app
    .wrapper
      main.hero
        h1.hero__title Ты сегодня покормил кота?
        Card
</template>

<script>
import Card from './components/Card.vue'

export default {
  name: 'App',
  components: {
    Card
  }
}
</script>

<style>

@font-face {
  font-family: "Trebuchet";
  src: url("assets/fonts/TrebuchetMS.woff") format("woff");
  font-weight: normal;
  font-style: normal;
}

@font-face {
  font-family: "Exo";
  src: url("assets/fonts/Exo20-Thin.woff") format("woff"); /* Modern Browsers */
  font-weight: normal;
  font-style: normal;
}

body {
  font-family: "Trebuchet";
  font-size: 16px;
  color: #666666;
  margin: 0;
  padding: 0;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
}

ul {
  list-style: none;
  padding: 0;
  margin: 0;
}

h1, h2 {
  margin: 0
}
p {
  margin: 0
}
.wrapper {
  background: url('assets/shadow.png');
	position: relative;
	padding: 40px;
	min-height: 100vh;
	display: flex;
	align-items: center;
  justify-content: center;
}

.hero__title {
  font-size: 42px;
  color: #ffffff;
  font-family: "Exo";
  text-align: center;
  filter: drop-shadow(0px 1px 0.5px #000000);
  margin-bottom: 20px;
}
	
</style>
