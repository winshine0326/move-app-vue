<template>
  <div class="search-box">
    <input
      type="search"
      placeholder="검색어 입력"
      @change="
        inputText = $event.target.value;
        $emit('search_movie', $event.target.value);
        $event.target.value = '';
      "
    />
    <!-- @input="inputText = $event.target.value" -->
    <!-- 사용자가 입력할 때 inputText에 추가-->
    <!-- v-model="변수" 사용자에게 입력 받은 값을 변수에 알아서 저장해줍니다.-->
    <button>검색</button>
  </div>
  <p>{{ inputText }}</p>
</template>
<script>
export default {
  name: "SearchBarComponent",
  emits: ["search_movie"],
  data() {
    return {
      inputText: "",
    };
  },
  props: {
    data: Array,
  },
  watch: {
    // 검사할 변수명(변경값, 이전값[optional]) {로직}
    inputText(name) {
      //입력한 영화제목이 데이터에 있는지 확인
      const findName = this.data.filter((movie) => {
        // 객체 안의 data는 앞에 this를 붙임
        return movie.title.includes(name);
      });
      console.log(findName);
      if (findName.length === 0) {
        alert("해당하는 영화가 없습니다");
      }
    },
  }, // watch는 특정 상태변수가 변경됨을 감지하는 hook
};
</script>
<style>
.search-box {
  display: flex;
  padding: 10px;
  justify-content: center;
}
.search-box input {
  padding: 5px 10px;
}

.search-box button {
  margin: 0;
}
</style>
