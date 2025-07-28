<template>
  <div class="event" :class="{ show: isOpen }">
    <!-- {클래스명 : 조건}-->
    <p>{{ text }}</p>
    <button @click="isOpen = false">X</button>
  </div>
</template>
<script>
export default {
  name: "EventComponent",
  props: {
    text: String,
  },
  data() {
    return {
      isOpen: true,
    };
  },
};
</script>
<style>
.event {
  background-color: #444;
  color: #fff;
  padding: 10px 20px;
  text-align: center;
  display: flex;
  justify-content: space-between;
  align-items: center;
  display: none;
}
.event p {
  margin: 0;
}

.show {
  display: flex;
}

.event button {
  margin: 0;
}
</style>
