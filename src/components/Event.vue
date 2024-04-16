<template>
  <div class="page-container">
    <div class="title">Eventos</div>
    <div class="canva-container">
      <iframe
        loading="lazy"
        :src="canvaEmbedSrc"
        allowfullscreen="allowfullscreen"
        allow="fullscreen"
      >
      </iframe>
    </div>
  </div>
</template>

<script>
export default {
  // eslint-disable-next-line vue/multi-word-component-names
  name: "Event",
  data() {
    return {
      canvaEmbedSrc: "https://www.canva.com/design/DAFv9JUIUZI/view?embed",
    };
  },
};
</script>

<style scoped>
.page-container {
  display: flex;
  flex-direction: column;
  justify-content: center;
  align-items: center;
  height: auto;
}

.canva-container {
  position: relative;
  width: 90%;
  height: 0;
  padding-top: 50%;
  padding-bottom: 0;
  box-shadow: 0 2px 8px 0 rgba(63, 69, 81, 0.16);
  overflow: hidden;
  border-radius: 8px;
  will-change: transform;
}

.canva-container iframe {
  position: absolute;
  width: 100%;
  height: 100%;
  top: 0;
  left: 0;
  border: none;
  padding: 0;
  margin: 0;
}

.title {
  text-align: center;
  font-size: 2rem;
  font-weight: 600;
  margin-bottom: 20px;
}
</style>
