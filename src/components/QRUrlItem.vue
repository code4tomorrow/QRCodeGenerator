<template>
  <div class="item" @click="openLink()">
    <img id="link" src="@/assets/icons/link.svg" />
    <div class="info">
      <h2 id="url-title">{{ this.urlTitle }}</h2>
      <div id="url">{{ this.url }}</div>
    </div>
  </div>
</template>

<script>
export default {
  name: "QRUrlItem",
  props: ["url"],
  data: () => {
    return {
      urlTitle: "",
    };
  },
  async created() {
    this.urlTitle = await this.getTitle(this.url);
  },
  methods: {
    getTitle(url) {
      return fetch(`https://cors-anywhere.herokuapp.com/${url}`)
        .then((res) => res.text())
        .then((html) => {
          const doc = new DOMParser().parseFromString(html, "text/html");
          const title = doc.querySelectorAll("title")[0];
          return title.innerText;
        });
    },
    openLink() {
      this.$emit("setCurrentURL", this.url);
      window.open(this.url, "_blank");
    },
  },
};
</script>

<style scoped>
.item {
  background: #f9fbfe;

  border-radius: 18px;
  box-shadow: 0 4px 6px 0 #d8dde3;

  text-align: left;

  display: flex;
  align-items: center;

  padding: 15px 25px;
  margin: 40px 0;

  cursor: pointer;
}

#link {
  width: 2rem;
  height: 2rem;
}

.info {
  margin-left: 20px;
  width: 85%;
}

#url-title {
  font-family: "Montserrat SemiBold";
  font-size: 1.4rem;
  margin: 0;

  white-space: nowrap;
  text-overflow: ellipsis;
  overflow: hidden;
}

#url {
  font-family: "Montserrat Light";

  white-space: nowrap;
  text-overflow: ellipsis;
  overflow: hidden;
}
</style>