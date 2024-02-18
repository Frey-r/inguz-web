<template>
  <div class="banner-image-container">
    <cielo class="cielo">
      <estrella class="estrella a">⭐</estrella>
      <estrella class="estrella b">⭐</estrella>
      <estrella class="estrella c">⭐</estrella>
      <planeta class="planeta">🪐</planeta>
    </cielo>
    <nave class="nave"> <span>🚀</span> </nave>
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
@keyframes scroll {
  from {
    transform: rotate(0deg);
  }
  to {
    transform: rotate(23deg) scale(20%, 200%) translate(-34px, -26px);
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

.nave {
  position: fixed;
  top: 51%;
  left: 13%;
  animation: nave 2s infinite ease-in-out;
  filter: drop-shadow(0px 0px 5px var(--inguz_green));
  span {
    font-size: 20vh;
  }
}
</style>

<script setup lang="ts"></script>
