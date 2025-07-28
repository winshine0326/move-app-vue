<template>
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
      <button @:click="increseLike(i)">좋아용👍</button>
      <span>{{ item.like }}</span>
      <p>
        <button
          @:click="
            isModal = true;
            selectedMovie = i;
          "
        >
          상세보기
        </button>
      </p>
    </div>
  </div>

  <div class="modal" v-if="isModal">
    <!-- 아니 개편하네 if가 html 속성에 있어 -->
    <div class="inner">
      <h3>{{ data[selectedMovie].title }}</h3>
      <p>영화 상세정보</p>
      <button @:click="isModal = false">닫기</button>
    </div>
  </div>
</template>

<script>
import data from "./assets/movies";
console.log(data);
export default {
  name: "App",
  data() {
    return {
      isModal: false,
      data,
      selectedMovie: 0,
    };
  },
  methods: {
    increseLike(i) {
      this.data[i].like += 1;
    },
  },
};
</script>

<style>
* {
  box-sizing: border-box;
  margin: 0;
}
body {
  max-width: 768px;
  margin: 0 auto;
}
h1,
h2,
h3 {
  margin-bottom: 1rem;
}
p {
  margin-bottom: 0.5rem;
}
button {
  margin-right: 10px;
  margin-top: 1rem;
}
.item {
  width: 100%;
  border: 1px solid #ccc;
  display: flex;
  margin-bottom: 20px;
  padding: 1rem;
}
.item figure {
  width: 30%;
  margin-right: 1rem;
}
.item img {
  width: 100%;
}
.item .info {
  width: 100%;
}

.modal {
  background-color: rgba(0, 0, 0, 0.7);
  position: fixed;
  left: 0;
  top: 0;
  width: 100%;
  height: 100vh;
  display: flex;
  justify-content: center;
  align-items: center;
}

.modal .inner {
  background-color: #fff;
  width: 80%;
  padding: 20px;
  border-radius: 10px;
}
</style>
