<template>
  <h1>영화 정보</h1>
  <div v-for="(item, i) in data" :key="i">
    <h2 class="bg-yellow" :style="item.textRed">{{ item.title }}</h2>
    <!-- 아니 속성값이 존재하지 않아도 에러가 나지 않는다고????? 혁신이다 -->
    <p>개봉 : {{ item.year }}</p>
    <p>장르 : {{ item.category }}</p>
    <button @:click="increseLike(i)">좋아용👍</button>
    <span>{{ item.like }}</span>
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
        },
        {
          title: "아쿠아맨과 로스트 킹덤",
          year: 2023,
          category: "액션, 판타지, 어드벤처",
          like: 0,
        },
        {
          title: "패배히로인이 너무 많아!",
          year: 2024,
          category: "러브코미디, 학원",
          like: 0,
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
.bg-yellow {
  background-color: yellow;
}
</style>
