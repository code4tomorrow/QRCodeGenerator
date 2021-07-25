<template>
  <div class="prompt">
    <input
      id="input-url"
      placeholder="Pass your link here..."
      v-model="inputURL"
    />
    <div id="dot" @click="saveURL()">
      <img id="send" src="@/assets/icons/send.svg" />
    </div>
  </div>
</template>

<script>
export default {
  data: () => {
    return {
      inputURL: "",
    };
  },
  methods: {
    saveURL() {
      this.$emit("addToHistory", this.inputURL);
      this.inputURL = "";
    },
  },
};
</script>

<style scoped>
.prompt {
  width: 100%;
  display: flex;
  align-items: center;
  justify-content: center;
}

#input-url {
  font-family: "Montserrat";

  width: 40%;
  height: 25px;
  margin-right: 10px;

  background: #fafafa;

  border: 1px solid #bfbfbf;
  border-radius: 22px;

  padding: 5px 15px;

  outline: none;
}

#dot {
  height: 40px;
  width: 40px;
  background-color: #e0e0e0;
  border-radius: 50%;

  border: 1px solid #cacaca;

  display: flex;

  align-items: center;
  justify-content: center;

  cursor: pointer;
}

#send {
  width: 50%;
  height: 50%;
  padding-left: 5px;
}
</style>