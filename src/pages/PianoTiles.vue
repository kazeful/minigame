<script setup lang="ts" generic="T extends any, O extends any">
import { GamePlay } from '~/composables/pianoTiles'

defineOptions({
  name: 'PianoTilesPage',
})

const play = new GamePlay()
</script>

<template>
  <div flex="~ gap1" items-center justify-center py5>
    <button btn @click="play.reset()">
      New Game
    </button>
  </div>

  <div ma h100 w81 border="gray 2" overflow="hidden">
    <div relative :style="{ top: `${play.state.value.top}px` }">
      <div
        v-for="row, y in play.board" :key="y"
        flex="~"
        items-center justify-center
      >
        <div
          v-for="block, x in row"
          :key="x"
          h25 w20
          border="gray 1"
          :class="block.isBlack ? 'bg-black' : 'bg-white'"
          @click="play.onClick(block)"
        >
          <!-- {{ block.x }},{{ block.y }} -->
        </div>
      </div>
    </div>
  </div>
</template>
