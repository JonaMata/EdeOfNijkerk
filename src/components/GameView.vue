<script>
import photos from "../assets/photos.json";

export default {
  name: "GameView",
  data() {
    return {
      score: 0,
      round: 0,
      correct: null,
      current: null,
      photos: [],
    };
  },
  methods: {
    newRound() {
      this.round++;
      if (this.photos.length < 1) {
        this.photos = photos;
      }
      let index = Math.floor(Math.random() * this.photos.length);
      this.current = this.photos[index];
      this.photos.splice(index, 1);
    },
    handleAnswer(answer) {
      if (this.current.place === answer) {
        this.score++;
        this.correct = true;
      } else {
        this.correct = false;
      }
      setTimeout(() => {
        this.correct = null;
      }, 2000);
      this.newRound();
    },
  },
  mounted() {
    this.photos = photos;
    this.newRound();
  },
};
</script>

<template>
  <div class="gameview">
    <div class="gameInfo">
      <span> Round: {{ round }} </span>
      <span> Score: {{ score }}/{{ round - 1 }} </span>
    </div>
    <div class="imgBox">
      <img v-if="correct === null" :src="'photos/' + current?.photo" />
      <div
        v-if="correct !== null"
        class="answer"
        :class="correct ? 'correct' : 'incorrect'"
      >
        <div>
          {{ correct ? "Correct!" : "Incorrect!" }}
        </div>
      </div>
    </div>
    <div class="buttons">
      <button @click="() => handleAnswer(0)">Ede</button>
      <button @click="() => handleAnswer(1)">Nijkerk</button>
    </div>
  </div>
</template>

<style lang="scss" scoped>
.gameInfo {
  width: 80vw;
  display: flex;
  flex-direction: row;
  justify-content: space-between;
  font-weight: bold;
  font-size: 1.2em;
}
.imgBox {
  height: 60vh;
  width: 80vw;
  background-color: #c1c1c1;
  display: flex;
  justify-content: center;
  align-items: center;

  & img {
    max-height: 100%;
    max-width: 100%;
  }
}
.answer {
  width: 100%;
  height: 100%;
  display: flex;
  flex-direction: column;
  justify-content: center;
  align-items: center;
  font-size: 5em;

  &.correct {
    background-color: #2bbc53;
    color: black;
  }

  &.incorrect {
    background-color: #bc3239;
    color: white;
  }
}
.buttons {
  width: 80vw;
  height: 20vh;
  display: flex;
  flex-direction: column;
  justify-content: space-evenly;
  align-items: center;

  & button {
    width: 100%;
    height: 2em;
    font-size: 1.2em;
    background-color: #3dbaff;
    border: #2d5973 solid 1px;
  }
}
</style>
