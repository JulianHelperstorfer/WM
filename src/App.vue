<template>
  <Suspense>
    <template #default>
      <Main />
    </template>
    <template #fallback>
      <span>Loading....</span>
    </template>
  </Suspense>
  <!--<div id="app">
    <Header />
    <Main />
    <Footer />
  </div>-->
</template>

<script>
import Main from './components/Main.vue';

export default {
  name: 'App',
  components: {
    Main,
  },
};
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
body {
  background: url('https://img.freepik.com/premium-vector/world-cup-2022-qatar-background_342897-24.jpg?w=2000')
    fixed; /* Set the background image and make it not move when scrolling */
  background-size: 100% 100%;
}
</style>
