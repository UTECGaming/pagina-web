<!-- App.vue -->
<template>
  <NavBar class="navbar"/>

  <div class="main-content">
    <Home class="content-item" id="home"/>
    <About class="content-item" id="about"/>
    <Game class="content-item" id="game"/>
    <Event class="content-item" id="event"/>
  </div>
</template>

<script>
import NavBar from './components/NavBar.vue';
import Home from './components/Home.vue';
import About from './components/About.vue';
import Game from './components/Game.vue';
import Event from './components/Event.vue';

export default {
  components: {
    NavBar,
    Home,
    About,
    Game,
    Event,
  },
};
</script>

<style scoped>
/* Estilos para tu aplicación principal */
@import url('https://fonts.googleapis.com/css2?family=Poppins:wght@300;400;500;600;700;800;900&display=swap');
* {
  margin: 0;
  padding: 0;
  box-sizing: border-box;
  font-family: 'Poppins', sans-serif;
}

body {
  min-width: 100vh;
  background: #f5f5f5;
  background-size: cover;
  background-position: center;
  margin: 0;
}

.main-content {
  display: flex;
  flex-direction: column;
  justify-content: center;
  padding: 80px 0px;
  z-index: 0;
}

.content-item {
  margin-bottom: 40px;
}

.navbar {
  z-index: 10;
}
</style>
