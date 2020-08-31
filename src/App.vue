<template>
  <div id="app" class="container">
    <NavBar />
    <Container />
  </div>
</template>

<script>
import Container from './components/Container.vue';
import NavBar from './components/NavBar.vue';

import 'bootstrap/dist/css/bootstrap.css';
import 'bootstrap-vue/dist/bootstrap-vue.css';

export default {
  name: 'App',
  components: {
    Container,
    NavBar,
  },
};
</script>

<style>
 @import url('./assets/styles/main.scss');
 @media (min-width: 1430px) {
  .container {
    display: flex;
    align-items: center;
    flex-direction: column;
  }
}
</style>
