<template>
  <div class="container">
    <sign-up></sign-up>
  </div>
</template>

<script>
import SignUp from "./layouts/SignUp";

export default {
  name: "App",
  components: {
    "sign-up": SignUp
  }
};
</script>

<style lang="scss">
@import url("https://fonts.googleapis.com/css2?family=IBM+Plex+Sans:wght@100;200;300;400;500;600;700&display=swap");

:root {
  --dc: rgb(32, 32, 32);
  --lc: #ebf4f8;
  --gc: #756f86;
  --bc: #0880ae;
}

* {
  margin: 0;
  padding: 0;
  font-family: "IBM Plex Sans", serif;
  font-style: normal;
  font-weight: normal;
}

.container {
  display: flex;
  justify-content: center;
  align-items: center;
}
</style>
