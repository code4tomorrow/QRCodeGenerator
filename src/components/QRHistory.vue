<template>
  <div class="history">
    <button @click="saveUrls()">Send to History</button>
    <input v-model="currentURL"/>
  </div>

</template>

<script>
export default {
  data: () => {
    return {
      urlList: JSON.parse(localStorage.getItem("URLs")) || [],
      currentURL: "https://github.com/code4tomorrow/javascript",
    }
  },
  created() {
    
  },
  methods: {
    saveUrls() {
      this.urlList.unshift(this.currentURL)
      localStorage.setItem("URLs", JSON.stringify(this.urlList))
    }
  }
};

</script>

<style>
</style>