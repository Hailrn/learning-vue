<template>
  <!-- <FormContainer
  @mouseenter="formHover"
  @mouseleave="formUnhover"
  /> -->
  <BookDisplay></BookDisplay>
</template>

<script>
import BookDisplay from './components/BookDisplay.vue';

// import FormContainer from './components/FormContainer.vue';

export default {
  name: 'App',
  components: {
    // FormContainer
    BookDisplay
  },
  // methods: {
  //   formHover() {
  //     document.body.classList.add('darken-bg');
  //   },
  //   formUnhover() {
  //     document.body.classList.remove('darken-bg');
  //   }
  // }
}
</script>

<style>
/* body {
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
} */

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
