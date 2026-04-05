<!-- <template>
  <div class="next">
    <button class="next-button">
      <img src="@/assets/btn.png" />
    </button>
  </div>
</template>

<script setup lang="ts"></script>

<style scoped>
/* .next {
  display: flex;
  align-items: center;
} */

.next-button {
  background: none;
  border: none;
  width: 80px;
  height: 80px;
  display: flex;
  justify-content: center;
  align-items: center;
  cursor: pointer;
}

.next-button img {
  width: 30px;
  height: 30px;
}
</style> -->

<template>
  <div class="next">
    <button class="next-button">
      <img src="@/assets/btn.png" />
    </button>
  </div>
</template>

<style scoped>
.next {
  display: flex;
  align-items: center;
  gap: 16px;
  margin-top: 0px;
  margin-bottom: 45px;
  padding-bottom: 20px;
  margin-left: auto;
  width: fit-content;
}

.next-button {
  width: 80px;
  height: 60px;
  background: none;
  border: none;
  cursor: pointer;
  display: flex;
  align-items: center;
  justify-content: center;
}
.next-button {
  transition: all 0.3s ease-out;
  -moz-transition: all 0.3s ease-out;
  -o-transition: all 0.3s ease-out;
  -webkit-transition: all 0.3s ease-out;
}

.next-button:hover {
  transform: scale(1.1);
  -webkit-transform: scale(1.1);
  -moz-transform: scale(1.1);
  -o-transform: scale(1.1);
}
</style>
