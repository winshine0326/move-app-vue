<template>
  <nav class="navbar">
    <a href="#">Home</a>
    <a href="#">Movies</a>
    <a href="#">About</a>
  </nav>
</template>
<script>
export default {
  name: "NavBarComponent",
};
</script>
<style>
.navbar {
  background: #000;
  width: 100%;
  padding: 20px;
  text-align: center;
}
.navbar a {
  color: #fff;
  text-decoration: none;
  padding: 1em;
}
</style>
