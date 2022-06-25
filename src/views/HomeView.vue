<script>
import GameView from "@/components/GameView.vue";
export default {
  components: { GameView },
  data() {
    return {
      playing: false,
    };
  },
  methods: {
    startGame() {
      this.playing = true;
    },
  },
};
</script>

<template>
  <main>
    <GameView v-if="playing" />
    <button v-if="!playing" @click="startGame">Start Game</button>
  </main>
</template>

<style lang="scss" scoped>
button {
  width: 100%;
  height: 2em;
  font-size: 1.2em;
  background-color: #3dbaff;
  border: #2d5973 solid 1px;
}
</style>
