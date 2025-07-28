<template>
  <div class="modal" v-if="isModal">
    <!-- 아니 개편하네 if가 html 속성에 있어 -->
    <div class="inner">
      <h3>{{ data[selectedMovie].title }}</h3>
      <p>영화 상세정보</p>
      <button @:click="$emit('closeModal')">닫기</button>
      <!-- $emit('이벤트명')으로 부모에게 이벤트 요청-->
    </div>
  </div>
</template>
<script>
export default {
  name: "ModalComponent",
  props: {
    selectedMovie: Number,
    data: Array,
    isModal: Boolean,
  },
};
</script>
<style lang=""></style>
