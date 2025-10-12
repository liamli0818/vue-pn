<template>
  <div>
    <ul>
      <li
        v-for="(link, index) in links"
        :key="index"
        class="card"
        @click="redirectTo(link.href)"
      >
        {{ link.name }}
      </li>
    </ul>
  </div>
  <svg style="display: none">
    <filter id="displacementFilter">
      <feTurbulence
        type="turbulence"
        baseFrequency="0.01"
        numOctaves="2"
        result="turbulence"
      />

      <feDisplacementMap
        in="SourceGraphic"
        in2="turbulence"
        scale="200"
        xChannelSelector="R"
        yChannelSelector="G"
      />
    </filter>
  </svg>
</template>

<script>
export default {
  name: "LinksNavigator",
  props: {
    links: {
      type: Array,
      required: true,
    },
  },
  methods: {
    redirectTo(href) {
      // Redirect to the provided link
      window.open(href, "_blank");
    },
  },
};
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
ul {
  padding: 0;
  display: flex;
  flex-direction: column;
  row-gap: 1em;
}
.card {
  cursor: pointer;
  align-self: center;
  width: 45%;
  box-sizing: border-box;
  flex-wrap: wrap;
  display: flex;
  align-items: center;
  justify-content: center;
  padding: 1em;
  overflow: hidden;
  border-radius: inherit;
  transition: opacity 0.26s ease-out;
  border-radius: 2em;
  filter: drop-shadow(-8px -10px 46px #0000005f);
  backdrop-filter: brightness(1.1) blur(2em) url(#displacementFilter);
}

.card::before {
  content: "";
  position: absolute;
  inset: 0;
  z-index: 0;
  overflow: hidden;
  border-radius: 2em;
  -webkit-box-shadow: inset 2px 2px 0px -2px rgba(255, 255, 255, 0.7),
    inset 0 0 3px 1px rgba(255, 255, 255, 0.7);
  box-shadow: inset 6px 6px 0px -6px rgba(255, 255, 255, 0.7),
    inset 0 0 8px 1px rgba(255, 255, 255, 0.7);
}
@media (orientation: portrait) {
  .card {
    width: 90%;
  }
}
</style>
