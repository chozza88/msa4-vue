<script setup>
import axios from "axios";
import { reactive, ref } from "vue";

const arr = [3, 4, 2, 5];
const data = ref([]); // null으로 초기값을 하면 v-for에서 제대로 참조 하지 못할 수도 있음.

async function getPicsum() {
  try {
    const url = "https://picsum.photos/v2/list?page=4&limit=10";
    const res = await axios.get(url);
    data.value.push(...res.data);
  } catch (error) {
    console.error(error);
  }
}
</script>

<template>
  <h1>리스트 랜더링</h1>
  <button type="button" @click="getPicsum">추가</button>
  <div class="container">
    <div class="card" v-for="item in data" :key="item.id">
      <div
        class="card-img"
        :style="{ backgroundImage: `url('${item.download_url}')` }"
      ></div>
      <span>
        {{ item.author }}
      </span>
    </div>
  </div>

  <!-- <div v-for="(value, key) in arr" :key="key">
    <p>{{ value }}</p>
  </div>

  <div v-for="value in 5">
    <p>{{ value }} 회</p>
  </div> -->
</template>

<style scoped>
/* 내상위의 component에 영향을 주지 않기 위해 scoped를 사용 이름도 list_container 처럼 사용 */
.container {
  padding: 20px;
  display: grid;
  grid-template-columns: repeat(auto-fill, minmax(200px, 1fr));
  gap: 10px;
}
.card {
  display: flex;
  flex-direction: column;
  justify-content: space-between;
  gap: 10px;
}
.card-img {
  padding-top: 60%;
  background-repeat: no-repeat;
  background-position: center;
  background-size: cover;
}
</style>
