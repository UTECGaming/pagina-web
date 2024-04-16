<template>
  <div class="about">
    <div class="title">¿Quiénes somos?</div>
    <div class="info">
      Somos una organización encargada de realizar eventos, con la finalidad de
      generar espacios de integración donde los estudiantes puedan no solo
      relajarse, sino también conocer nuevas personas, mejorar sus habilidades
      de trabajo en equipo, comunicación asertiva y autoconfianza.
    </div>

    <div class="two-columns">
      <div class="column">
        <div class="title">Misión</div>
        <p class="info">
          Crear eventos y grupos sociales en los que se reconozca el valor de los videojuegos como una herramienta para mejorar las habilidades blandas dentro de la comunidad estudiantil de UTEC.
        </p>
      </div>
      <div class="column">
        <div class="title">Visión</div>
        <p class="info">
          Ser una organización que sea reconocida por el valor que genera dentro del alumnado de UTEC.
        </p>
      </div>
    </div>
  </div>
</template>
  
<script>
export default {
  // eslint-disable-next-line vue/multi-word-component-names
  name: "About",
};
</script>
  
<style scoped>
.about {
    flex: 1;
    display: flex;
    flex-direction: column;
    justify-content: center;
    align-items: center;
    padding: 20px;
}
.title {
    text-align: center;
    font-size: 2rem;
    font-weight: 600;
}
.info {
    width: 770px;
    text-align: justify;
    font-size: 1.2rem;
    line-height: 1.5;
    margin-bottom: 20px;
}

.two-columns {
  display: flex;
  justify-content: center;
  margin-top: 20px;
}

.column {
  flex: 1;
  padding: 0 80px;
}
.column .info {
  width: 300px;
  margin: 0 auto;
  text-align: justify;
  font-size: 1.2rem;
  line-height: 1.5;
}

@media (max-width: 820px) {
  .two-columns {
    flex-direction: column;
  }
  .column {
    padding: 0;
  }
  .column .info, .info {
    width: 100%;
  }

  .column .info {
    margin-bottom: 20px;
  }
}
</style>
  