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

        "Super Smash Bros. es un juego de lucha crossover que reúne a personajes de diversas franquicias de Nintendo y otras compañías para combatir en escenarios dinámicos. Ofrece modos multijugador y para un solo jugador, enfocándose en la acción y diversión.",

        "Mario Kart 8 Deluxe es un juego de carreras colorido y frenético protagonizado por los personajes de Nintendo. Con una amplia selección de pistas y modos de juego, ofrece diversión para jugadores de todas las edades.",

        "Crash Team Racing Nitro-Fueled es un juego de carreras lleno de adrenalina que ofrece emocionantes pistas y desafíos. Con personajes del universo de Crash Bandicoot, es una experiencia competitiva y divertida para todos.",

        "JoJo's All Star Battle R es un juego de lucha que celebra el manga/anime 'JoJo's Bizarre Adventure'. Presenta personajes de todas las sagas enfrentándose en combates estilizados con habilidades únicas y movimientos dramáticos.",

        "Left 4 Dead 2 es un juego de disparos en primera persona cooperativo que enfrenta a los jugadores contra hordas de zombis en una lucha por la supervivencia a través de distintos escenarios post-apocalípticos. Incluye nuevas armas, campañas y modos de juego.",

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
  overflow: hidden;
  text-overflow: ellipsis;
  max-width: 100%;
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
    min-height: 600px;
  }
  .card h1 {
    margin-top: 1em;
    line-height: 1em;
  }
  .card p{
    font-size: 1em;
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
  .card {
    padding: 0;
    min-height: 550px;
  }
  .card h1 {
    margin-top: 0.5em;
    line-height: 1em;
    font-size: 2em;
  }
  .card p {
    font-size: 1em;
    line-height: 1.25em;
  }
  .game-slider {
    font-size: 13px;
  }
  .game-img {
    height: 180px;
  }
}
</style>