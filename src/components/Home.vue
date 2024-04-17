<template>
  <div class="img-container">
    <transition name="fade" mode="out-in">
      <img
        :key="currentIndex"
        :src="require(`../assets/img${currentIndex + 1}.jpeg`)"
        alt="current_image"
        class="img-bg"
      />
    </transition>
    <img
      :src="require(`../assets/img${currentIndex + 1}.jpeg`)"
      alt="next"
      class="img-bg next"
    />
    <img src="../assets/UG_Blanco.png" class="img-logo" />
  </div>
</template>
  
<script>
export default {
  // eslint-disable-next-line vue/multi-word-component-names
  name: "Home",
  data() {
    return {
      currentIndex: 0,
      nextIndex: 1,
      images: [
        "../assets/img1.jpeg",
        "../assets/img2.jpeg",
        "../assets/img3.jpeg",
      ],
    };
  },
  created() {
    setInterval(this.changeImage, 5000);
  },
  methods: {
    changeImage() {
      this.currentIndex = (this.currentIndex + 1) % this.images.length;
      this.nextIndex = (this.nextIndex + 1) % this.images.length;
    },
  },
};
</script>
  
<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
.img-container {
  position: relative;
  display: flex;
  justify-content: center;
  align-items: center;
  width: 100%;
  height: 75vh;
}

.img-bg {
  background-size: cover;
  background-position: center;
  background-repeat: no-repeat;
  filter: brightness(0.3);

  width: 100%;
  height: 100%;

  object-fit: cover;
  overflow: hidden;
}
.next {
  position: absolute;
  filter: brightness(0.3);
  z-index: -1;
}

.img-logo {
  position: absolute;
  width: auto;
  height: 100%;
  top: 50%;
  left: 50%;
  transform: translate(-50%, -50%);
}

.fade-enter-active,
.fade-leave-active {
  transition: opacity 0.5s;
}

.fade-enter, .fade-leave-to {
  opacity: 0;
}
@media screen and (max-width: 700px) {
  .img-container {
    height: 50vh;
  }
}
</style>
  