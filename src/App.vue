<template>
  <div class="app">
    <Header />
    <Sprite />
  </div>
</template>

<script>

import Header from "./components/Header";
import Sprite from "./svg/sprite";
export default {
  name: 'App',
  components: {
    Sprite,
    Header

  }
}
</script>

<style>
* {
  box-sizing: border-box;
}
body {
  background: #f5f5f5;
}
</style>
