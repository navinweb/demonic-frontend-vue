<template>
  <div id="app">
    <Nav></Nav>
    <router-view/>
  </div>
</template>

<script>
import Nav from '@/components/common/Nav';

export default {
  name: 'App',
  components: {
    Nav,
  },
};
</script>

<style>
  #app {
    max-width: 1024px;
    width: 100%;
    margin: 20px auto;
    padding: 0 15px
  }
</style>
