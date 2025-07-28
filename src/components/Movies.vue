<template lang="">
  <div class="container">
    <h1>영화 정보</h1>
    <div v-for="(item, i) in data" :key="i" class="item">
      <figure>
        <img :src="item.imgUrl" :alt="item.title" />
      </figure>
      <div class="info">
        <h2 class="bg-yellow" :style="item.textRed">{{ item.title }}</h2>
        <!-- 아니 속성값이 존재하지 않아도 에러가 나지 않는다고????? 혁신이다 -->
        <p>개봉 : {{ item.year }}</p>
        <p>장르 : {{ item.category }}</p>
        <button @:click="$emit('increseLike', i)">좋아용👍</button>
        <span>{{ item.like }}</span>
        <p>
          <button @:click="$emit('openModal', i)">상세보기</button>
        </p>
      </div>
    </div>
  </div>
</template>
<script>
export default {
  name: "MoviesComponent",
  props: {
    data: Array,
    isModal: Boolean,
    selectedMovie: Number,
  },
};
</script>
<style>
.container {
  padding: 20px;
}
</style>
