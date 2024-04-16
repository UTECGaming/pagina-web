<template>
  <div class="game-slider">
    <div class="card">
      <div class="game">
        <div class="game-img-cnt">
          <img
            class="game-img"
            :src="require(`../assets/game${slideIndex + 1}.png`)"
            :alt="$data.games[slideIndex]"
          />
        </div>

        <div class="game-details">
          <div>
            <h1 class="game-name">
              {{ $data.games[slideIndex] }}
            </h1>

            <p class="game-description">
              {{ $data.gameDescription[slideIndex] }}
            </p>
          </div>
        </div>
      </div>

      <div class="arrow-left" @click="slideLeft">
        <i class="fa fa-arrow-left"></i>
      </div>

      <div class="arrow-right" @click="slideRight">
        <i class="fa fa-arrow-right"></i>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  // eslint-disable-next-line vue/multi-word-component-names
  name: "Game",
  data() {
    return {
      slideIndex: 0,
      games: [
        "Overcooked",
        "Just Dance",
        "Dragon Ball Fighter Z",
        "Super Smash Bros Ultimate",
        "Mario Kart 8 Deluxe",
        "Crash Team Racing Nitro Fueled",
        "Jojo’s All Star Battle R",
        "Left 4 Dead 2",
        "Pokemon Go",
      ],
      gameDescription: [
        "Overcooked!, Overcooked! 2 y todos sus DLC’s vuelven mezclados y remasterizados para crear esta deliciosa edición definitiva! Disfruta de cientos de niveles de caos culinario cooperativo mientras cocinas en sitios peligrosos y sombríos.",

        "Just Dance es un juego de ritmo, donde tendrás que demostrar tus habilidades para el baile y ser el mejor. Podrás bailar al ritmo de canciones de diferentes artistas como “BTS”, “Harry Styles”, “Linkin Park”, “K/DA” y muchos más.",

        "Dragon Ball Fighter Z conserva la esencia de la famosa saga Dragon Ball: espectaculares combates entre poderosos luchadores. Demuestra tus habilidades en este emocionante juego de pelea.",

        "Super Smash Bros Ultimate reúne a una amplia variedad de personajes icónicos de diferentes franquicias de videojuegos. El juego ofrece combates rápidos y emocionantes, con nuevos ataques y opciones defensivas. Los jugadores pueden enfrentarse en batallas uno contra uno o en combates multijugador con hasta ocho jugadores.",

        "Mario Kart 8 Deluxe es un videojuego de carreras donde podrás escoger entre diferentes personajes clásicos de Nintendo y modificar todas las partes de tu kart a tu gusto. El juego ofrece una amplia variedad de modos de juego, incluyendo el modo para un jugador y el modo multijugador. Puedes competir contra la computadora o jugar con hasta 12 jugadores en línea.",

        "Crash Team Racing Nitro-Fueled es una versión remasterizada del juego original de Crash Team Racing, lanzado en 1999 para la consola PlayStation. El juego cuenta con una amplia selección de personajes jugables, incluyendo a Crash Bandicoot y sus amigos, así como a sus enemigos. Tendrás diferentes tipos de motor para escoger el que se adapte mejor a tu modo de juego.",

        "¡Jonathan Joestar, Jotaro Kujo, DIO, Jolyne Cujoh y otros personajes de JOJO´s Bizarre Adventure se reúnen a través de diferentes generaciones!¡Con 50 personajes jugables de todos los arcos, puedes revivir las batallas más populares de cada historia y ver a los personajes de los diferentes universos interactuar por primera vez!",

        "Ambientado en el apocalipsis zombi, Left 4 Dead 2 (L4D2) es la esperadísima secuela del galardonado Left 4 Dead, el juego cooperativo número 1 de 2008. Este FPS cooperativo de acción y terror te llevará a ti y a tus amigos por las ciudades, pantanos y cementerios donde tendrán que enfrentar diferentes tipos de hordas de infectados, infectados especiales y el poderoso Tank! Podrán reunir un gran arsenal de armas para defenderse, pero lo más importante es el trabajo en equipo.",

        "Como parte de la franquicia Pokémon, Pokémon GO es un popular juego de realidad aumentada con el objetivo de que los jugadores usen configuraciones basadas en la ubicación del GPS para atrapar y entrenar personajes Pokémon.",
      ],
    };
  },
  methods: {
    slideLeft() {
      this.slideIndex--;
      if (this.slideIndex < 0) {
        this.slideIndex = this.games.length - 1;
      }
    },
    slideRight() {
      this.slideIndex++;
      if (this.slideIndex > this.games.length - 1) {
        this.slideIndex = 0;
      }
    },
  },
};
</script>

<style scoped>
.game-slider {
  display: flex;
  justify-content: center;
  align-items: center;
  padding: 2em;
}

.card {
  padding: 2em;
  width: 90vw;
  height: auto;
  max-width: 1050px;
  position: relative;
  background: linear-gradient(
    45deg,
    rgb(255, 255, 255) 0%,
    rgb(221, 223, 227) 40%,
    rgba(244, 255, 245, 0.8)
  );
  border-radius: 2em;
}

.game {
  position: relative;
  z-index: 2;
  display: grid;
  grid-template-columns: 0.6fr 1fr;
  grid-column-gap: 50px;
  justify-content: center;
  align-self: center;
  color: #103248;
  margin: 30px;
  padding: 30px;

  opacity: 1;
  transition: opacity 0.5s ease;
}
.game-img {
  display: flex;
  justify-content: center;
  align-items: center;
  width: auto;
  height: 25vw;
  overflow: hidden;
}
.game-img img {
  filter: drop-shadow(0 0 3em rgba(0, 0, 0, 0.3));
}

.game-description {
  /* ... otras propiedades ... */
  overflow: hidden; /* Oculta el texto que no cabe en el contenedor */
  text-overflow: ellipsis; /* Agrega puntos suspensivos al final del texto */
  max-width: 100%; /* Asegura que el texto no desborde el contenedor */
}

.game h1 {
  font-size: 2.8em;
  margin: 0;
}

.arrow-left,
.arrow-right {
  position: absolute;
  top: 50%;
  transform: translateY(-100%);
  width: 4em;
  height: 4em;
  background: black;
  color: #fff;
  border-radius: 100%;
  text-align: center;
  line-height: 4.2em;
  z-index: 2;
  transition: 0.3s;
  cursor: pointer;
}

.arrow-left i,
.arrow-right i {
  font-size: 1.5em;
}

.arrow-left {
  left: -1.5em;
}

.arrow-right {
  right: -1.5em;
}

.arrow-left:hover,
.arrow-right:hover {
  color: #10afcf;
}

.title {
  text-align: center;
  font-size: 2rem;
  font-weight: 600;
  margin-bottom: -20px;
}

@media screen and (max-width: 880px) {
  .card {
    text-align: center;
    height: initial;
    padding: 0em 0em 1em 2em;
  }
  .card h1 {
    margin-top: 1em;
  }
  .game-details,
  .game-img-cnt {
    display: flex;
    justify-content: center;
    align-items: center;
  }
  .game {
    grid-template-columns: 1fr;
  }
}

@media screen and (max-width: 700px) {
  .game-slider {
    font-size: 13px;
  }
}
</style>