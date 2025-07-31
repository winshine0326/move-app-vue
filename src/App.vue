<template>
  <NavBar />
  <Event :text="text" />
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
      text: "와우ㅏ우ㅏ우ㅏ우ㅏ우",
    };
  },
  methods: {
    increseLike(i) {
      this.data[i].like += 1;
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
