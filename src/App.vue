<template>
  <div class="background">
    <video autoplay muted loop playsinline class="background-video">
      <source src="./assets/bg1.mp4" type="video/mp4" />
    </video>
    <div class="footer">©2025 Developed by LiamLi</div>
  </div>
  <div class="content">
    <h1>Projects Navigator</h1>
    <LinksNavigator :links="links" />
  </div>
</template>

<script>
import LinksNavigator from "./components/LinksNavigator.vue";
import LinksJSON from "./assets/links.json";

export default {
  name: "App",
  components: {
    LinksNavigator,
  },
  data() {
    return {
      links: LinksJSON,
    };
  },
};
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: rgba(255, 255, 255, 0.5);
  font-size: 1em;
  margin-top: 60px;
}
.background {
  position: absolute;
  width: 100vw;
  height: 100vh;
  top: 0;
  left: 0;
  z-index: -1;
  overflow: hidden;
}
.background-video {
  filter: brightness(0.5);
}
.content {
}
.footer {
  background: rgba(255, 255, 255, 0.5);
  padding: 0.5em 0;
  text-align: center;
  width: 100%;
  position: absolute;
  bottom: 0;
  left: 0;
}
</style>
