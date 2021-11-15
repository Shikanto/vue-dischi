<template>
  <div id="app">
    <header class="header-container">
      <img src="./assets/spoty-logo.png" alt="">
    </header>
    <div class="main-container">
      <div class="container">
        <DiscContainer></DiscContainer>
      </div>
    </div>
  </div>
</template>

<script>

import DiscContainer from "./components/DiscContainer.vue";

export default {
  name: "App",
  components: {
    DiscContainer,
  },
};
</script>

<style lang="scss">
@import "styles/app.scss";

.header-container{
  background-color: $background-header;

  img{
    width: 120px;
    height: 100px;
  }
}

.main-container{
  background-color:$background-main;
  padding: 100px 0;
}

</style>
