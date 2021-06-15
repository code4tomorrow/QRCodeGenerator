<template>
  <div id="app">
    <img alt="Vue logo" src="./assets/logo.png" />
    <QRPrompt />
    <QRHistory />
    <vue-qrcode draggable="false" :width="300" :value="currentURL" />
  </div>
</template>

<script>
import QRPrompt from "@/components/QRPrompt.vue";
import QRHistory from "@/components/QRHistory.vue";

import VueQrcode from "vue-qrcode";

export default {
  name: "App",
  components: {
    QRPrompt,
    QRHistory,
    VueQrcode,
  },
  data: () => {
    return {
      currentURL: "https://github.com/code4tomorrow/javascript",
    };
  },
  mounted() {},
  methods: {
    setURL(url) {
      this.currentURL = url;
    },
  },
};
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
