<script setup>
const pos = document.documentElement;
pos.addEventListener('mousemove', (e) => {
  pos.style.setProperty('--x', e.clientX + 'px');
  pos.style.setProperty('--y', e.clientY + 'px');
});
</script>
<template>
  <div
    class="w-[100vw] h-[100vh] relative bg-black flex justify-center items-center"
  >
    <div class="text-white text-[12em] cursor-default">今天是KFC疯狂星期四</div>
    <div class="light"></div>
  </div>
</template>

<style scoped>
.light {
  position: fixed;
  top: 0;
  left: 0;
  width: 100%;
  height: 100%;
  background: radial-gradient(
    circle at var(--x) var(--y),
    transparent 10%,
    rgba(0, 0, 0, 0.95) 20%
  );
}
</style>
