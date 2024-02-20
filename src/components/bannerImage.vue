<template>
  <div id="banner-image-container" @click="openBackground">
    <cielo id="cielo">
      <estrella class="estrella a">⭐</estrella>
      <estrella class="estrella b">⭐</estrella>
      <estrella class="estrella c">⭐</estrella>
      <planeta class="planeta">🪐</planeta>
    </cielo>
    <nave id="nave"> <span>🚀</span> </nave>
  </div>
</template>

<style>
@keyframes nave {
  0% {
    transform: rotate(-23deg) translate(34px, -26px);
    filter: drop-shadow(0px 0px 60px var(--inguz_green));
  }
  50% {
    transform: rotate(-23deg) translate(-34px, 26px);
    filter: drop-shadow(0px 0px 43px var(--inguz_green));
  }
  100% {
    transform: rotate(-23deg) translate(34px, -26px);
    filter: drop-shadow(0px 0px 60px var(--inguz_green));
  }
}
@keyframes naveOut {
  0% {
    transform: rotate(-23deg) translate(34px, -26px);
    filter: drop-shadow(0px 0px 60px var(--inguz_green));
  }
  100% {
    transform: rotate(-40deg) translate(35svw, -66svh);
  }
}
@keyframes cieloOut {
  to {
    font-size: 0;
    opacity: 0;
  }
}
@keyframes scroll {
  from {
    transform: rotate(23deg);
  }
  to {
    transform: rotate(0deg) scale(200%);
  }
}
.estrella {
  position: fixed;
  &.a {
    top: 54svh;
    left: 10svw;
    font-size: 6svh;
    transform: rotate(-21deg);
  }
  &.b {
    top: 71svh;
    left: 36svw;
    font-size: 12svh;
    transform: rotate(-7deg);
  }
  &.c {
    top: 97svh;
    left: 10svw;
    font-size: 10svh;
    transform: rotate(-45deg);
  }
}
planeta.planeta {
  position: fixed;
  top: 43svh;
  left: 31svw;
  font-size: 7svh;
  transform: rotate(-19deg);
}

nave {
  position: fixed;
  top: 51%;
  left: 13%;
  animation: nave 2s infinite ease-in-out;
  span {
    font-size: 20vh;
  }
}
</style>

<script setup lang="ts">
const openBackground = () => {
  let { style } = document.getElementById("banner-image-container");
  let bodyStyle = document.body.style;
  let textStyle = document.body.style;
  let banner = document.getElementById("banner-image-container");
  naveOut();
  starsOut();
  setTimeout(() => {
    style.animation = "scroll 2s ease-in";
    style.zIndex = "-1";
    setTimeout(() => {
      bodyStyle.backgroundColor = "#11131d";
      bodyStyle.color = "whitesmoke";
      if (banner) {
        banner.remove();
      }
    }, 2000);
    setTimeout(() => {
      window.scrollBy({
        top: window.innerHeight * 1,
        behavior: "smooth",
        duration: 500,
      });
    }, 1900);
  }, 1900);
};
const naveOut = () => {
  let nave = document.getElementById("nave");
  let { style } = document.getElementById("nave");
  style.animation = "naveOut 2s ease-out";
  setTimeout(() => {
    nave.remove();
  }, 1900);
};
const starsOut = () => {
  let { style } = document.getElementById("cielo");
  let cielo = document.getElementById("cielo");
  style.animation = "cieloOut 1s ease-out";
  setTimeout(() => {
    cielo.remove();
  }, 990);
};
</script>
