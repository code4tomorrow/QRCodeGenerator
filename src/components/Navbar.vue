<template>
  <div class="navbar">
    <img
      id="logo"
      src="@/assets/logo.svg"
      @click="goTo('https://code4tomorrow.org/')"
    />
    <div>
      <img
        class="icon"
        src="@/assets/icons/github.svg"
        @click="goTo('https://github.com/code4tomorrow/QRCodeGenerator')"
      />
    </div>
  </div>
</template>

<script>
export default {
  name: "Navbar",
  methods: {
    goTo(url) {
      window.location.href = url;
    },
  },
};
</script>

<style scoped>
.navbar {
  display: flex;
  background: #78a1bb;

  height: 5rem;

  align-items: center;
  justify-content: space-around;
}

img {
  cursor: pointer;
}

#logo {
  width: 4rem;
  height: 4rem;
}

.icon {
  width: 2.5rem;
  height: 2.5rem;

  margin: 0 20px;
}
</style>