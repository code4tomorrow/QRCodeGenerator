<template>
  <div class="history">
    <QRUrlItem
      v-for="(url, index) in urlList"
      :key="url + index"
      :url="url"
      @setCurrentURL="setCurrentURL"
    />
  </div>
</template>

<script>
import QRUrlItem from "@/components/QRUrlItem.vue";

export default {
  props: ["urlList"],
  components: {
    QRUrlItem,
  },
  methods: {
    setCurrentURL(url) {
      this.$emit("setCurrentURL", url);
    },
  },
};
</script>

<style scoped>
.history {
  width: 50%;
  height: 85vh;
  overflow-x: auto;
}
</style>