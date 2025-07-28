<template>
  <h1 class="bg-yellow" :style="textRed">{{ title }}</h1>
  <p>개봉 : {{ year }}</p>
  <p>장르 : {{ category }}</p>
</template>

<script>
export default {
  name: "App",
  data() {
    return {
      title: "노량",
      year: 2025,
      category: "액션, 드라마",
      textRed: { color: "red" }, // 객체로 넘겨야함
    };
  },
};
</script>

<style>
.bg-yellow {
  background-color: yellow;
}
</style>
