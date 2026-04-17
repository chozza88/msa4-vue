<script setup>
// js 코드 작성 부분
import ConditionalRendering from "./components/ConditionalRendering.vue";
import DataBinding from "./components/DataBinding.vue";
import EventHandling from "./components/EventHandling.vue";
import ListRandering from "./components/ListRandering.vue";
import Watchers from "./components/Watchers.vue";
</script>

<template>
  <!-- html 작성 부분 -->
  <DataBinding v-if="false" />
  <EventHandling v-if="false" />
  <ConditionalRendering v-if="false" />
  <ListRandering v-if="false" />
  <Watchers />
</template>

<style>
/* css 작성부분 */
</style>
