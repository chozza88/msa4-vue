<script setup>
import {
  onBeforeMount,
  onBeforeUnmount,
  onBeforeUpdate,
  onMounted,
  onUnmounted,
  onUpdated,
  ref,
} from "vue";

const cnt = ref(0);

onBeforeMount(() => {
  // 데이터를 백엔드에서 적은양을 받을 때 사용
  console.log("onBeforeMount", cnt.value);
});

onMounted(() => {
  // 그런데.. 데이터가 많을 때에는 화면이 먼저보여야... 사용자는 사이트가 괜찮다고 인식
  cnt.value++;
  console.log("onMounted", cnt.value);
});

onBeforeUpdate(() => {
  console.log("onBeforeUpdate");
});

onUpdated(() => {
  console.log("onUpdated");
});

onBeforeUnmount(() => {
  console.log("onBeforeUnmount");
});
onUnmounted(() => {
  console.log("onUnmounted");
});
</script>

<template>
  <h1>라이프 사이클: {{ cnt }}</h1>
  <button type="button" @click="cnt++">증가</button>
</template>

<style></style>
