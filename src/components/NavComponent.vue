<template>
  <nav>
    <div class="icon_logo">
      <button :type="button" @click="openNav">
        <img :src="require('@/assets/inguz.svg')" alt="Icon Logo" />
      </button>
    </div>
    <div class="nav-bar">
      <ul>
        <li>
          <a @mouseenter="checkWidth" @mouseleave="resetWidth">INICIO</a>
        </li>
        <li>
          <a @mouseenter="checkWidth" @mouseleave="resetWidth">CONTACTANOS</a>
        </li>
        <li>
          <a @mouseenter="checkWidth" @mouseleave="resetWidth"
            >SOBRE NOSOTROS</a
          >
        </li>
      </ul>
    </div>
  </nav>
</template>
<style>
:root {
  --inguz_green: #99ca3b;
  --inguz_pink: #b93ec6;
}
nav {
  margin: 70px;
  display: flex;
  align-items: center;
  height: 80px;
  font-size: 32px;
  font-weight: bolder;
}
.icon_logo {
  z-index: 2;
}
button {
  display: flex;
  align-items: center;
  justify-content: center;
  background: white;
  border-radius: 100%;
  border: solid black 6px;
  height: 80px;
  width: 80px;
  &:hover {
    img {
      transform: scale(1.2);
    }
  }
  img {
    width: 50px;
    height: auto;
    background: transparent;
  }
}
.nav-bar {
  display: none;
  align-items: center;
  height: 100%;
  background-color: black;
  li {
    list-style-type: none;
  }
  ul {
    display: flex;
    justify-content: space-evenly;
    width: 100%;
  }
  a {
    color: white;
    text-decoration: none;
    position: relative;
    display: inline-block;
    z-index: 2;

    &:after {
      content: "";
      display: block;
      position: fixed;
      height: 20px;
      z-index: -1;
      transform: translate(7px, -21px);
      transition: width 0.3s ease;
    }
    &.highlighted::after {
      width: var(--text-width, 0);
      background-color: var(--inguz_pink);
    }
  }
}
.open {
  display: flex;
  width: 80%;
  &:before {
    content: "";
    display: block;
    width: 40px;
    height: 80px;
    background-color: black;
    margin-right: 20px;
    transform: translateX(-38px);
  }
  &:after {
    content: "";
    display: block;
    width: 0;
    height: 0;
    border-right: 80px solid transparent;
    border-top: 80px solid black;
    position: fixed;
    transform: translateX(1903px);
  }
}
</style>
<script setup lang="ts">
function openNav(event: MouseEvent): void {
  let nav_bar = document.getElementsByClassName("nav-bar")[0];
  if (nav_bar) {
    nav_bar.classList.toggle("open");
  }
}
function checkWidth(event: MouseEvent) {
  const target = event.currentTarget as HTMLElement;
  const textWidth = target.offsetWidth;

  // Aplicar clase para resaltar y establecer la variable CSS
  target.classList.add("highlighted");
  target.style.setProperty("--text-width", `${textWidth}px`);
}
function resetWidth(event: MouseEvent) {
  const target = event.currentTarget as HTMLElement;
  target.classList.remove("highlighted");
}
</script>
