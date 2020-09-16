<template>
  <div id="app">
    <h1>Internship Signup Form</h1>
    <div class="line"></div>
    <SignUp msg="Prepare for your career with a Project Management, Web-Development, Graphic design, or Digital Marketing internship at Northern."/>
  </div>
</template>

<script>
import SignUp from './components/SignUp.vue'

export default {
  name: 'App',
  components: {
    SignUp
  }
}
</script>

<style>
@import url('https://fonts.googleapis.com/css2?family=Merriweather&family=Montserrat:wght@400;700&display=swap');
#app {
  
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;

  font-family: 'Merriweather', sans-serif;
  color: white;
  margin-left:10%;
  margin-right:10%;
}
html{
  background-color: #282828;
}
h1{
  font-family: 'Montserrat', sans-serif;
  font-size: 65px;
  text-transform: uppercase;
  color: white;
  margin-top: 10%;
}

.line{
  border-bottom: 10px solid #D02035;
  width:30%;
}
</style>
