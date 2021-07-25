<template>
  <div id="app">
    <Navbar />
    <div class="main">
      <QRHistory :urlList="urlList" @setCurrentURL="setCurrentURL" />
      <div class="right">
        <QRPrompt @addToHistory="addToHistory" />
        <vue-qrcode
          class="qr"
          draggable="false"
          :width="300"
          :value="currentURL"
        />
      </div>
    </div>
  </div>
</template>

<script>
import Navbar from "@/components/Navbar.vue";

import QRPrompt from "@/components/QRPrompt.vue";
import QRHistory from "@/components/QRHistory.vue";

import VueQrcode from "vue-qrcode";

export default {
  name: "App",
  components: {
    QRPrompt,
    QRHistory,
    VueQrcode,
    Navbar,
  },
  data: () => {
    return {
      currentURL: "www.github.com",
      urlList: JSON.parse(localStorage.getItem("URLs")) || [],
    };
  },
  created() {
    console.log(
      "Go here to enable cores: https://cors-anywhere.herokuapp.com/"
    );
  },
  methods: {
    addToHistory(url) {
      this.currentURL = url;
      this.urlList.unshift(url);

      localStorage.setItem("URLs", JSON.stringify(this.urlList));
    },
    setCurrentURL(url) {
      this.currentURL = url;
    },
  },
};
</script>

<style>
* {
  margin: 0;
  padding: 0;
}

@font-face {
  font-family: "Montserrat";
  src: url("../public/fonts/Montserrat/Montserrat-Regular.ttf");
}

@font-face {
  font-family: "Montserrat Light";
  src: url("../public/fonts/Montserrat/Montserrat-Light.ttf");
}

@font-face {
  font-family: "Montserrat SemiBold";
  src: url("../public/fonts/Montserrat/Montserrat-SemiBold.ttf");
}

.main {
  flex: 5;
  display: flex;
  margin: 1rem 10rem 0 10rem;
}

.right {
  flex: 5;
  display: flex;
  flex-direction: column;
  align-items: center;
  justify-content: center;
}
</style>
