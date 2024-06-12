<script setup>
function isMobile() {
  const userAgent = navigator.userAgent || navigator.vendor || window.opera;
  return /android|webos|iphone|ipad|ipod|blackberry|iemobile|opera mini/i.test(
    userAgent.toLowerCase()
  );
}

const pos = document.documentElement;

function updateLightPosition(x, y) {
  pos.style.setProperty('--x', x + 'px');
  pos.style.setProperty('--y', y + 'px');
}

//获取屏幕大小
const screenWidth = window.screen.width;
const screenHeight = window.screen.height;

if (isMobile()) {
  console.log('用户正在使用移动设备');
  pos.addEventListener('touchmove', (e) => {
    const touch = e.touches[0];
    console.log('Touch position:', touch.clientX, touch.clientY); // 调试输出
    updateLightPosition(touch.clientX, touch.clientY);
  });
  updateLightPosition(screenWidth / 2, screenHeight / 2);
} else {
  console.log('用户正在使用桌面设备');
  pos.addEventListener('mousemove', (e) => {
    console.log('Mouse position:', e.clientX, e.clientY); // 调试输出
    updateLightPosition(e.clientX, e.clientY);
  });
}
</script>

<template>
  <div
    class="w-[100vw] min-h-[100vh] relative bg-black flex justify-center items-center"
  >
    <div class="text-white md:text-[10rem] text-[3rem] cursor-default">
      KFC疯狂星期四!
    </div>
    <div class="light"></div>
  </div>
</template>

<style scoped>
.light {
  position: fixed;
  top: 0;
  left: 0;
  right: 0;
  bottom: 0;
  width: 100%;
  height: 100%;
  background: radial-gradient(
    circle at var(--x) var(--y),
    transparent 10%,
    rgba(0, 0, 0, 0.95) 20%
  );
  pointer-events: none; /* 确保触摸事件穿透 */
}
</style>
