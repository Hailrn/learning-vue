<template>
  <!-- <img alt="Vue logo" src="./assets/logo.png"> -->
  <!-- <div id="background-changer">
    <button @click="backgroundChanger">Ganti Warna Backgroundnya!</button>
  </div> -->
  <!-- <div id="color-changer">
    <input v-model="color" type="color">
    <button @click="textColorChanger">Ganti Warna Textnya!</button>
  </div> -->
  <FormContainer
  @mouseenter="formHover"
  @mouseleave="formUnhover"
  />
</template>

<script>
import FormContainer from './components/FormContainer.vue';

export default {
  name: 'App',
  // data() {
  //   return {
  //     color : "#000000"
  //   }
  // },
  components: {
    FormContainer
  },
  methods: {
    formHover() {
      document.body.classList.add('darken-bg');
    },
    formUnhover() {
      document.body.classList.remove('darken-bg');
    }
  //   backgroundChanger() {
  //     let rgb = []
  //     for (let i = 0; i<3; i++) {
  //       rgb.push(Math.round(Math.random() * 255))
  //     }
  //     document.body.style.backgroundColor = `rgb(${rgb[0]}, ${rgb[1]}, ${rgb[2]})`
  //   },
  //   textColorChanger() {
  //     document.getElementById("app").style.color = this.color;
  //   }
  }
}
</script>

<style>
body {
  background-image: url("/public/wallpaper/natlan.jpg");
  background-size: cover;
  background-repeat: no-repeat;
  transition: all 2s;
}

body::before {
  content: '';
  position: absolute;
  top: 0;
  left: 0;
  right: 0;
  bottom: 0;
  background-color: rgba(0, 0, 0, 0);
  transition: background-color 0.5s ease;
  z-index: -1;
}

body.darken-bg::before {
  background-color: rgba(0, 0, 0, 0.5);
}

#app {
  font-family: 'Gill Sans', 'Gill Sans MT', Calibri, 'Trebuchet MS', sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #4f4a4a;
  height: 98.3vh;
  display: flex;
  justify-content: center;
  align-items: center;
}

</style>
