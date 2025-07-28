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
    </div>
  </div>
</template>

<script>
export default {
  name: "App",
  data() {
    return {
      data: [
        {
          title: "노량",
          year: 2025,
          category: "액션, 드라마",
          textRed: { color: "red" },
          like: 0,
          imgUrl: "./assets/노량.jpeg",
        },
        {
          title: "아쿠아맨과 로스트 킹덤",
          year: 2023,
          category: "액션, 판타지, 어드벤처",
          like: 0,
          imgUrl: "./assets/아쿠아맨.webp",
        },
        {
          title: "패배히로인이 너무 많아!",
          year: 2024,
          category: "러브코미디, 학원",
          like: 0,
          imgUrl: "./assets/패배히로인.jpeg",
        },
      ],
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
</style>
