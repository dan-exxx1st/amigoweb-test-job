<template>
  <sign-up></sign-up>
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
  --bc: #0880ae;
}

* {
  margin: 0;
  padding: 0;
}
</style>
