<template>
  <NavBar />
  <Event :text="text[eventTextNum]" />
  <SearchBar :data="data_temp" @search_movie="searchMovie($event)" />
  <p class="showAllBtn">
    <button @click="showAllMovie()">전체보기</button>
  </p>
  <Movies
    :data="data_temp"
    :isModal="isModal"
    :selectedMovie="selectedMovie"
    @openModal="
      isModal = true;
      selectedMovie = $event;
    "
    @increseLike="increseLike($event)"
  />
  <!-- emit 파라미터를 받을 때는 $event -->

  <Modal
    :selectedMovie="selectedMovie"
    :data="data"
    :isModal="isModal"
    @closeModal="isModal = false"
  />
  <!-- emit 문법 -->
</template>

<script>
import data from "./assets/movies";
import NavBar from "./components/NavBar.vue";
import Modal from "./components/Modal.vue";
import Event from "./components/Event.vue"; // 이벤트 박스
import Movies from "./components/Movies.vue";
import SearchBar from "./components/SearchBar.vue"; //검색창

console.log(data);
export default {
  name: "App",
  data() {
    return {
      isModal: false,
      data,
      data_temp: [...data], //사본
      selectedMovie: 0,
      text: [
        "애니메이션 캐릭터를 위한 온라인 추모공간 커뮤니티, 최애의 사인",
        "디즈니 100주년 기념작, 위시",
        "그날, 대한민국의 운명이 바뀌었다, 서울의 봄",
      ],
      eventTextNum: 0,
      interval: null,
    };
  },
  methods: {
    increseLike(id) {
      this.data.find((movie) => {
        if (movie.id === id) {
          movie.like += 1;
        }
      });
    },
    searchMovie(title) {
      // 영화제목이 포함된 데이터를 가져옴
      this.data_temp = this.data.filter((movie) => {
        return movie.title.includes(title);
      });
    },
    showAllMovie() {
      this.data_temp = this.data;
    },
  },
  components: {
    NavBar: NavBar,
    Modal: Modal,
    Event: Event,
    Movies: Movies,
    SearchBar: SearchBar,
  },
  mounted() {
    console.log("mounted");
    this.interval = setInterval(() => {
      this.eventTextNum = (this.eventTextNum + 1) % this.text.length;
    }, 3000);
  },
  unmounted() {
    clearInterval(this.interval); //인터발 해제
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

.showAllBtn {
  width: 100%;
  display: flex;
  justify-content: center;
}
</style>
