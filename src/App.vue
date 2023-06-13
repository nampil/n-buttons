<template>
  <main>
    <h1>Buttons, a bunch of them!</h1>
    <div class="main-container">
      <section
        v-for="(tipo, index) in sections.filter((s) => s.name !== 'pathdraw')"
        :id="tipo.name"
        :class="['container', `tipo${index + 1}`]"
      >
        <button
          v-for="(btn, index) in btns"
          :key="index"
          :class="['btn', { circle: index === btns.length - 1 }]"
          :style="`
          --h1: ${btn.colors[0].h};
          --s1: ${btn.colors[0].s}%;
          --l1: ${btn.colors[0].l}%;
          --a1: ${btn.colors[0].a};
          --h2: ${btn.colors[1].h};
          --s2: ${btn.colors[1].s}%;
          --l2: ${btn.colors[1].l}%;
          --a2: ${btn.colors[1].a};
          --clr-h:  ${btn.colors[0].h};
          --clr-s:  ${btn.colors[0].s}%;
          --clr-l:  ${btn.colors[0].l}%;
          --clr-a:  ${btn.colors[0].a};
          --border: 2px;
          --border-radius: ${getBorderRadiusLast(index)}px;
          `"
          :data-text="btn.text"
        >
          <span>{{ btn.text }}</span>
          <i :class="`fa-solid fa-${btn.icon}`"></i>
        </button>
      </section>

      <section class="container tipo8">
        <button
          v-for="(btn, index) in btns"
          :key="index"
          :id="`btn-${index}`"
          :class="[
            'btn animate',
            index === btns.length - 1 ? 'circle' : 'rect',
            { pill: index === btns.length - 2 },
          ]"
          :style="`
        --h1: ${btn.colors[0].h};
        --s1: ${btn.colors[0].s}%;
        --l1: ${btn.colors[0].l}%;
        --a1: ${btn.colors[0].a};
        --h2: ${btn.colors[1].h};
        --s2: ${btn.colors[1].s}%;
        --l2: ${btn.colors[1].l}%;
        --a2: ${btn.colors[1].a};
        --clr-h:  ${btn.colors[0].h};
        --clr-s:  ${btn.colors[0].s}%;
        --clr-l:  ${btn.colors[0].l}%;
        --clr-a:  ${btn.colors[0].a};
        --border: 3px;
        --border-radius: ${getBorderRadiusLast(
          index,
          (isPill = index === btns.length - 2)
        )}px;
        `"
          :data-text="btn.text"
        >
          <span>{{ btn.text }}</span>
          <i :class="`fa-solid fa-${btn.icon}`"></i>
          <svg class="circle-svg" viewBox="0 0 100 100">
            <circle class="circle" cx="50" cy="50" r="48" fill-opacity="0" />
          </svg>

          <svg class="rect-svg">
            <rect
              x="1"
              y="1"
              rx="0"
              width="100%"
              height="100%"
              fill="none"
              stroke-width="2"
            />
          </svg>
        </button>
      </section>
    </div>
  </main>
</template>
<script setup>
import { nextTick, ref } from 'vue'

const sections = ref([
  { showCode: false, name: 'lighting' },
  { showCode: false, name: 'neumorphism' },
  { showCode: false, name: 'squareUp' },
  { showCode: false, name: 'spacial' },
  { showCode: false, name: 'skew' },
  { showCode: false, name: 'oldTv' },
  { showCode: false, name: 'pushUp' },
  { showCode: false, name: 'pathdraw' },
])

const colors = [
  [
    { h: 2, s: 65, l: 44, a: 1 },
    { h: 212, s: 80, l: 42, a: 1 },
  ],
  [
    { h: 324, s: 100, l: 50, a: 1 },
    { h: 323, s: 19, l: 24, a: 1 },
  ],
  [
    { h: 272, s: 76, l: 53, a: 1 },
    { h: 260, s: 100, l: 44, a: 1 },
  ],
  [
    { h: 164, s: 35, l: 19, a: 1 },
    { h: 152, s: 77, l: 77, a: 1 },
  ],
  [
    { h: 350, s: 81, l: 42, a: 1 },
    { h: 275, s: 66, l: 13, a: 1 },
  ],
  [
    { h: 6, s: 89, l: 51, a: 1 },
    { h: 41, s: 92, l: 53, a: 1 },
  ],
  [
    { h: 261, s: 45, l: 57, a: 1 },
    { h: 161, s: 61, l: 46, a: 1 },
  ],
]
const colors2 = [
  [
    { h: 0, s: 0, l: 20, a: 1 },
    { h: 0, s: 80, l: 48, a: 1 },
  ],
  [
    { h: 199, s: 85, l: 42, a: 1 },
    { h: 28, s: 85, l: 58, a: 1 },
  ],
  [
    { h: 348, s: 97, l: 63, a: 1 },
    { h: 230, s: 96, l: 62, a: 1 },
  ],
  [
    { h: 4, s: 78, l: 66, a: 1 },
    { h: 16, s: 82, l: 73, a: 1 },
  ],
  [
    { h: 348, s: 83, l: 59, a: 1 },
    { h: 44, s: 100, l: 87, a: 1 },
  ],
  [
    { h: 187, s: 72, l: 50, a: 1 },
    { h: 245, s: 36, l: 45, a: 1 },
  ],
  [
    { h: 204, s: 47, l: 45, a: 1 },
    { h: 48, s: 100, l: 74, a: 1 },
  ],
]

const getRandom = (arr) => {
  const length = arr.length

  const ramdonN = Math.floor(Math.random() * length)
  return arr[ramdonN]
}

const icons = [
  'paper-plane',
  'file-lines',
  'check',
  'cart-shopping',
  'store',
  'play',
  'stop',
  'binoculars',
  'arrow-rotate-left',
  'paintbrush',
  'angle-left',
  'angle-right',
]

const btns = [
  { text: 'Send', colors: getRandom(colors), icon: 'paper-plane' },
  { text: 'Report', colors: getRandom(colors), icon: 'file-lines' },
  { text: 'Save', colors: getRandom(colors2), icon: 'check' },
  { text: 'Buy', colors: getRandom(colors2), icon: 'cart-shopping' },
  { text: 'Sell', colors: getRandom(colors), icon: 'store' },
  { text: 'Play', colors: getRandom(colors), icon: 'play' },
  { text: 'Stop', colors: getRandom(colors), icon: 'stop' },
  { text: 'View more', colors: getRandom(colors), icon: 'binoculars' },
  { text: 'Undo', colors: getRandom(colors), icon: 'arrow-rotate-left' },
  { text: 'Print', colors: getRandom(colors), icon: 'paintbrush' },
  { text: 'Back', colors: getRandom(colors), icon: 'angle-left' },
  { text: 'Next', colors: getRandom(colors2), icon: 'angle-right' },
]

const getBorderRadiusLast = (n, isPill) => {
  let borderRadius = (n * 2).toString()
  if (n === btns.length - 2) {
    borderRadius = '99'
    let id = `btn-${n}`
    nextTick(() => {
      const btn = document.getElementById(id)
      if (isPill) {
        let height = btn.clientHeight
        borderRadius = (height / 2).toString()
        btn.style.setProperty('--border-radius', borderRadius + 'px')
      }
    })
  }
  return borderRadius
}

const toggleCode = (tipo) => {
  const target = sections.value.filter((section) => section.name === tipo)[0]
  target.showCode = !target.showCode
}
</script>

<style lang="scss">
*,
*::after,
*::before {
  box-sizing: border-box;
}
:root {
  --border-color: hsl(0, 0%, 55%);
  --clr-primary: hsl(202, 85%, 43%);
  --clr-neutral: hsl(0, 0%, 90%);
}
body {
  min-height: 100vh;
  margin: 0;
  display: flex;
  justify-content: center;
  align-items: center;
  font-family: Helvetica, sans-serif;
}
.main-container {
  max-width: 1120px;
  box-shadow: 0px 0px 10px 0px rgba($color: #000000, $alpha: 0.2);
  margin-bottom: 4rem;
}
.container {
  padding: 6rem;
  position: relative;
  display: flex;
  flex-wrap: wrap;
  justify-content: center;
  align-items: center;
  gap: 40px;
  @media screen and (max-width: 600px) {
    gap: 30px;
    padding: 3rem;
  }
}

h1 {
  margin-block: 4rem;
  @media screen and (max-width: 1120px) {
    padding: 3rem;
    margin-block: 2rem;
  }
}

.btn {
  --grad: linear-gradient(
    to right bottom,
    hsla(var(--h1), var(--s1), var(--l1), var(--a1)),
    hsla(var(--h2), var(--s2), var(--l2), var(--a2))
  );
  --clr: hsla(var(--clr-h), var(--clr-s), var(--clr-l), var(--clr-a));
  display: inline-flex;
  align-items: center;
  justify-content: center;
  gap: 0.5em;
  padding: 1em 1.5em;
  font-family: inherit;
  font-size: 1rem;
  position: relative;
  border: none;
  border-radius: var(--border-radius);
  cursor: pointer;
  &:focus-visible {
    outline: none;
  }

  &.circle {
    width: 7ch;
    padding: 1em;
    aspect-ratio: 1;
    border-radius: 100% !important;

    &::after,
    &::before {
      border-radius: 100% !important;
    }
    span {
      display: none;
    }
  }
}
.container.tipo1 {
  background-color: black;
  .btn {
    --full: linear-gradient(red 0 0);
    --border: 3px;
    background: var(--grad) border-box;
    color: transparent;
    border: var(--border) solid transparent;
    -webkit-background-clip: text;
    background-clip: text;
    box-shadow: 0px 0px 15px rgba(255, 255, 255, 0.3);
    transition: all 150ms ease-in;
    z-index: 1;
  }

  .btn::after {
    position: absolute;
    inset: calc(var(--border) * -1);
    border: inherit;
    border-radius: inherit;
    background: inherit;
    background-clip: border-box;
    -webkit-mask: var(--full) padding-box, var(--full);
    -webkit-mask-composite: xor;
    mask: var(--full) padding-box exclude, var(--full);
    content: '';
  }
  .btn:hover,
  .btn:focus-visible {
    color: #fff;
    outline: none;
  }

  .btn::before {
    content: '';
    position: absolute;
    inset: calc(var(--border) * -1);
    background: var(--grad) border-box;
    border-radius: var(--border-radius);
    z-index: -1;
    /* transform-origin: left center;
      transform: translateX(-10%) scaleX(0.7); */
    clip-path: circle(10%);
    transition: all 150ms ease-out;
    opacity: 0;
  }
  .btn:hover::before,
  .btn:focus-visible::before {
    opacity: 1;
    clip-path: circle(100%);
  }
}
.container.tipo2 {
  background-color: #e5e7e7;

  .btn {
    text-transform: uppercase;
    border: none;
    padding: 1.1em 1.6em;
    background: linear-gradient(145deg, #f5f7f7, #ced0d0);
    box-shadow: 10px 10px 10px #c3c4c4, -10px -10px 10px #ffffff;
    transform: scale(0.9);
    transition: all 250ms ease-out;
  }
  .btn:hover,
  .btn:focus-visible {
    box-shadow: 12px 12px 15px #c3c4c4, -6px -6px 12px #ffffff;
    transform: scale(1);
    outline: none;
  }
}

.container.tipo3 {
  background-color: #f4f4f4;
  .btn {
    background-color: transparent;
    border: var(--border) solid var(--clr);
    position: relative;
    z-index: 1;
    color: var(--clr);
    transition: 200ms ease-out;
    &:before {
      content: '';
      border-radius: var(--border-radius);
      position: absolute;
      inset: -1px;
      background: var(--clr) border-box;
      border: 3px;
      transform-origin: bottom;
      transform: scale(0.5, 0);
      z-index: -1;
      transition: 200ms ease-out;
    }
    &:hover,
    &:focus-visible {
      color: #fff;
    }
    &:hover:before,
    &:focus-visible:before {
      transform: scale(1);
    }
  }
}
.container.tipo4 {
  background-color: #ffffff;
  .btn {
    border: 2px solid transparent;
    background: transparent;
    color: var(--clr);
    position: relative;
    transition: all 200ms ease-out;
    z-index: 1;
    transform-style: preserve-3d;
    box-shadow: 0px 0px 10px hsla(var(--h1), var(--s1), var(--l1), 0.2),
      0px 0px 20px hsla(var(--h2), var(--s2), var(--l2), 0.1);

    &:before {
      content: '';
      position: absolute;
      border-radius: var(--border-radius);
      border-top: 2px solid var(--clr);
      border-right: 2px solid var(--clr);
      inset: -2px;
      z-index: -1;
      transition: 200ms ease-out;
      transform-origin: top right;
      transform: translateZ(-1px) scale(0);
    }
    &:after {
      content: '';
      position: absolute;
      border-radius: var(--border-radius);
      border-left: 2px solid var(--clr);
      border-bottom: 2px solid var(--clr);
      inset: -2px;
      z-index: -1;
      transition: 200ms ease-out;
      transform-origin: bottom left;
      transform: translateZ(-1px) scale(0);
    }
    &:hover,
    &:focus-visible {
      box-shadow: 0px 0px 0px var(--clr);
    }
    &:hover:before,
    &:focus-visible:before,
    &:hover:after,
    &:focus-visible:after {
      transform: translateZ(-1px) scale(1);
    }
  }
}

.container.tipo5 {
  background-color: #f4f4f4;
  .btn {
    transform: skew(-15deg);
    color: #fff;
    background-color: hsl(var(--h1), var(--s1), var(--l1));
    transition: 200ms ease-out;
    &:hover,
    &:focus-visible {
      background-color: hsl(var(--h1), var(--s1), calc(var(--l1) * 0.6));
      transform: skew(-5deg);
    }
  }
}
.container.tipo6 {
  --timing: 125ms;
  background-color: #ffffff;
  .btn {
    color: rgb(99, 99, 99);
    background-color: hsl(var(--h1), var(--s1), 90%);
    transition: 200ms ease-out;
    z-index: 1;
    &::after {
      content: '';
      position: absolute;
      top: 50%;
      left: 0;
      width: 100%;
      height: 3px;
      border-radius: var(--border-radius);
      background-color: hsl(var(--h1), var(--s1), 60%);
      z-index: -1;
      transform-origin: left center;
      transform: scaleX(0) translateY(-50%);
      transition: transform var(--timing) var(--timing) ease-out,
        height var(--timing) ease-out;
    }
    &:hover,
    &:focus-visible {
      color: rgb(255, 255, 255);
    }
    &:hover::after,
    &:focus-visible::after {
      transform: scaleX(1) translateY(-50%);
      height: 100%;
      transition: transform var(--timing) ease-out,
        height var(--timing) var(--timing) ease-out;
    }
  }
}

.container.tipo7 {
  background-color: #f4f4f4;

  .btn {
    color: hsl(0, 0%, 20%);
    background: #fff;
    transition: 200ms ease-out;
    box-shadow: 2px 2px 6px -2px rgba(0, 0, 0, 0.4);

    &:hover,
    &:focus-visible {
      color: var(--clr);
      transform: translate(-4px, -4px);
      box-shadow: 4px 4px 0px 0 var(--clr),
        2px 2px 4px 2px rgba(102, 102, 102, 0.4);
    }
  }
}
.container.tipo8 {
  background-color: #ffffff;

  .btn {
    border: none;
    background: #e4e4e4;

    transition: 250ms ease-out;
    svg {
      display: block;
      position: absolute;
      width: 100%;
      height: 100%;
      inset: 0;
      stroke-dasharray: 400;
      stroke-dashoffset: -400;
      transition: 400ms ease-out;
      stroke: var(--clr);
      stroke-width: var(--border);
    }
    &.rect {
      svg.rect-svg rect {
        width: calc(100% - var(--border));
        height: calc(100% - var(--border));
        rx: var(--border-radius);
      }

      svg.circle-svg {
        display: none;
      }
    }
    &.circle svg.rect-svg {
      display: none;
    }
  }

  .btn:hover,
  .btn:focus-visible {
    background: transparent;
    color: var(--clr);
  }
  .btn.animate:hover svg,
  .btn.animate:focus-visible svg {
    stroke-dashoffset: 0;
  }
}

.slide-enter-active,
.slide-leave-active {
  transition: transform 250ms ease-out;
  transform: translateX(0);
}
.slide-enter-from,
.slide-leave-to {
  transform: translateX(100%);
}
</style>
