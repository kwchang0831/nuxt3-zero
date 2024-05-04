<script setup lang="ts">
import { onMounted, ref } from 'vue'
import { Application, Assets, Container, Sprite } from 'pixi.js'

const pixiContainer = ref<HTMLElement | null>(null)
const app = new Application()

onMounted(async () => {
  await app.init({ backgroundAlpha: 0, resizeTo: window })

  pixiContainer.value?.appendChild(app.canvas)

  const container = new Container()

  app.stage.addChild(container)

  const texture = await Assets.load('https://pixijs.com/assets/bunny.png')

  // Create a 5x5 grid of bunnies in the container
  for (let i = 0; i < 25; i++) {
    const bunny = new Sprite(texture)

    bunny.x = (i % 5) * 40
    bunny.y = Math.floor(i / 5) * 40
    container.addChild(bunny)
  }

  // Move the container to the center
  container.x = app.screen.width / 2
  container.y = app.screen.height / 2

  // Center the bunny sprites in local container coordinates
  container.pivot.x = container.width / 2
  container.pivot.y = container.height / 2

  // Listen for animate update
  app.ticker.add((time) => {
    // Continuously rotate the container!
    // * use delta to create frame-independent transform *
    container.rotation -= 0.01 * time.deltaTime
  })
})
</script>

<template>
  <div relative h-full w-full bg-black text-white>
    <client-only>
      <div ref="pixiContainer" absolute right-0 top-0 z-99 h-full w-full />
    </client-only>
    <div h-full flex select-none text-center all:transition-400>
      <div ma>
        <div animate-bounce-alt animate-duration-1s animate-count-infinite text-5xl fw100>
          UnoCSS
        </div>
        <div>
          Testing...123
          <div i-svg-spinners:12-dots-scale-rotate />
        </div>

        <div m1 text-lg fw300 op30>
          The instant on-demand Atomic CSS engine.
        </div>
        <div m2 flex justify-center text-2xl op30 hover="op80">
          <a i-carbon-logo-github text-inherit href="https://github.com/unocss/unocss" target="_blank" />
        </div>
      </div>
    </div>
    <div absolute bottom-5 left-0 right-0 text-center fw300 op30>
      on-demand · instant · fully customizable
    </div>
  </div>
</template>

<style lang="scss">
html,
body,
#__nuxt,
#__layout {
  height: 100% !important;
  width: 100% !important;
}
</style>
