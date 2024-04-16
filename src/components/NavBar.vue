<!-- NavBar.vue -->
<template>
  <header class="header">
    <nav class="nav">
      <a class="logo">UTEC Gaming</a>

      <button class="nav-toggle" @click="toggleNav" :aria-label="ariaLabel">
        <i class="fa fa-bars"></i>
      </button>

      <ul class="nav-menu" :class="{ 'nav-menu_visible': isMenuVisible }">
        <li class="nav-menu-item">
          <a @click="scrollToElement('home')" class="nav-menu-link">
            Inicio
          </a>
        </li>

        <li class="nav-menu-item">
          <a @click="scrollToElement('about')" class="nav-menu-link">
            Acerca de
          </a>
        </li>
        
        <li class="nav-menu-item">
          <a @click="scrollToElement('game')" class="nav-menu-link">
            Juegos
          </a>
        </li>
        
        <li class="nav-menu-item">
          <a @click="scrollToElement('event')" class="nav-menu-link">
            Eventos
          </a>
        </li>
      </ul>
    </nav>
  </header>
</template>

<script>
export default {
  data() {
    return {
      isMenuVisible: false,
    };
  },
  methods: {
    scrollToElement(elementId) {
      const element = document.getElementById(elementId);
      if (element) {
        const headerHeight = document.querySelector('.header').offsetHeight + 20;
        const elementPosition = element.getBoundingClientRect().top + window.scrollY;

        window.scrollTo({
          top: elementPosition - headerHeight,
          behavior: 'smooth',
        });

        this.isMenuVisible = false;
      }
    },
    toggleNav() {
      this.isMenuVisible = !this.isMenuVisible;
    },
  },
  computed: {
    ariaLabel() {
      return this.isMenuVisible ? "Cerrar menú" : "Abrir menú";
    },
  },
};
</script>

<style scoped>
.header {
  position: fixed;
  top: 0;
  left: 0;

  width: 100%;
  height: 80px;

  background: black;
  box-shadow: 0 4px 8px rgba(0, 0, 0, 0.5);
}

.nav {
  display: flex;
  justify-content: space-between;

  width: 100%;
  margin: auto;
}

.logo {
  font-size: 32px;
  font-weight: bold;
  color: #fff;
  padding: 0 40px;
  line-height: 80px;
}

.nav-menu {
  display: flex;
  margin-right: 40px;
  list-style: none;
}

.nav-menu-item {
  font-size: 18px;
  margin: 0 10px;
  line-height: 50px;
  text-transform: uppercase;
  width: max-content;
}

.nav-menu-link {
  position: relative;
  font-size: 18px;
  color: #fff;
  font-weight: 500;
  text-decoration: none;
  margin-left: 40px;
}

.nav-menu-link::before {
  content: '';
  position: absolute;
  top: 100%;
  left: 0;
  width: 0;
  height: 2px;
  background: #00bede;
  transition: .3s;
}

.nav-menu-link:hover::before {
  width: 100%;
}

.nav-toggle {
  color: white;
  background: none;
  border: none;
  font-size: 30px;
  padding: 0 20px;
  line-height: 60px;
  cursor: pointer;

  display: none;
}

@media (max-width: 1125px) {
  body {
    padding-top: 70px;
  }

  .header {
    height: 60px;
  }

  .logo {
    font-size: 25px;
    padding: 0 20px;
    line-height: 60px;
  }

  .nav-menu {
    flex-direction: column;
    align-items: center;
    margin: 0;
    background-color: #00262c;
    position: fixed;
    top: 60px;
    width: 100%;
    padding: 20px;

    height: calc(100% - 60px);
    overflow-y: auto;

    left: 100%;
    transition: left 0.3s;
  }

  .nav-menu-item {
    margin-left: -70px;
    line-height: 70px;
  }

  .nav-menu-link:hover,
  .nav-menu-link_active {
    background: none;
    color: #00bede;
  }

  .nav-toggle {
    display: block;
  }

  .nav-menu_visible {
    left: 0;
  }

  .nav-toggle:focus:not(:focus-visible) {
    outline: none;
  }
}
</style>
