<template>
  <div id="app">
    <nav>
      <router-link to="/home">Home</router-link> | 
      <router-link to="/products">Products</router-link>
    </nav>
    <router-view />
  </div>
</template>

<script>
export default {
  name: 'App',
};
</script>

<style>
nav {
  margin-bottom: 10px;
  padding: 10px;
  background-color: grey;
}
</style>