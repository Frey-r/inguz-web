<template>
  <nav class="nav-body">
    <div class="icon_logo">
      <button type="button" @click="openNav">
        <img :src="require('@/assets/inguz.svg')" alt="Icon Logo" />
      </button>
    </div>
    <div class="nav-bar">
      <ul>
        <li>
          <a @mouseenter="checkWidth" @mouseleave="resetWidth">INICIO</a>
        </li>
        <li>
          <a
            class="color-verde"
            @mouseenter="checkWidth"
            @mouseleave="resetWidth"
            >CONTACTANOS</a
          >
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
@keyframes horizontalBounce {
  0% {
    transform: translateX(0);
  }
  50% {
    transform: translateX(-6%);
  }
  100% {
    transform: translateX(0);
  }
}

.color-verde {
  color: var(--inguz_green) !important;
}
nav {
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
  background: white !important;
  border-radius: 100%;
  border: solid black 6px;
  height: 80px;
  width: 80px;
  img {
    transition: transform 0.3s ease-in-out;
  }
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
  &:focus-visible {
    outline: none;
  }
  &:after {
    content: "👈 click para abrir el navegador";
    position: fixed;
    left: 6.5%;
    font-size: var(--font-size-medium);
    font-weight: lighter;
    animation: horizontalBounce 1.2s ease-in-out infinite;
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
      height: 16px;
      z-index: -1;
      transform: translate(7px, -25px);
      transition: all 0.2s ease;
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
    transform: translateX(var(--nav-width));
  }
}
</style>
<script setup lang="ts">
function openNav(): void {
  let nav_bar = document.getElementsByClassName("nav-bar")[0];
  let nav = document.getElementsByClassName("nav-body")[0];
  const styleSheet = document.styleSheets[0];
  styleSheet.insertRule(
    "button::after { display: none; }",
    styleSheet.cssRules.length
  );

  if (nav_bar) {
    nav_bar.classList.toggle("open");
    navWidth();
    if (nav_bar.classList.contains("open")) {
      nav.style.setProperty(
        "filter",
        "drop-shadow(4px 7px 0px var(--inguz_pink))"
      );
    } else {
      nav.style.setProperty("filter", "drop-shadow(0px 0px 0px transparent)");
    }
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
function navWidth() {
  let target = document.getElementsByClassName("nav-bar")[0];
  let navWidth = target.offsetWidth;
  target.style.setProperty("--nav-width", `${navWidth}px`);
}
</script>
