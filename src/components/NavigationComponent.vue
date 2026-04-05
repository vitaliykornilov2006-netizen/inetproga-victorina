<script setup lang="ts">
const props = defineProps<{
  results: (boolean | null)[]
}>()
</script>

<template>
  <div class="contr">
    <div class="navpoloska">
      <div
        v-for="(res, i) in props.results"
        :key="i"
        class="segment"
        :style="{
          background: res === null ? 'transparent' : res ? '#6bff2f' : '#ff3b3b',
        }"
      ></div>
    </div>

    <div class="mrkrs">
      <div class="mrr" v-for="n in props.results.length + 1" :key="n"></div>
    </div>
  </div>
</template>

<style>
.contr {
  margin: 39px 82px;
}
.navpoloska {
  /* Rectangle 3.2 */
  position: relative;
  width: 940px;
  height: 6px;

  overflow: hidden;
  background: #0096ec;
  border-radius: 10px;
  display: flex;
}
.zelenka {
  /* Rectangle 3.3 */

  width: 235px;
  height: 6px;

  background: #6bff2f;
  border-radius: 10px 0px 0px 10px;
}
.mrkrs {
  width: 940px;
  display: flex;
  justify-content: space-between;
}

.mrr {
  width: 2px;
  height: 12px;
  background-color: #0096ec;
}

.segment {
  flex: 1;
  height: 100%;
  transition: background 0.3s;
}
</style>
