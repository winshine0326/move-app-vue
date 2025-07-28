<template>
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
export default {
  name: "ModalComponent",
};
</script>
<style lang=""></style>
