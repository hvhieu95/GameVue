<template>
  <div id="app">
    <div class="wrapper clearfix">
      <players
        v-bind:scoresPlayer="scoresPlayer"
        v-bind:currentScore="currentScore"
        v-bind:activePlayer="activePlayer"
      />
      <controls
        v-on:handleNewGame="handleNewGame"
        v-on:handleRollDice="handleRollDice"
      />
      <dices v-bind:dices="dices" />
      <popup-rule
        v-on:handleConfirm="handleConfirm"
        v-bind:isOpenPopup="isOpenPopup"
      />
    </div>
  </div>
</template>

<script>
import Players from "./components/Players.vue";
import Controls from "./components/Controls.vue";
import Dices from "./components/Dices.vue";
import PopupRule from "./components/PopupRule.vue";
export default {
  name: "app",
  data() {
    return {
      scoresPlayer: [10, 55],
      currentScore: 30,
      activePlayer: 0,
      dices: [2, 6],
      isPlaying: false,
      isOpenPopup: false,
    };
  },
  components: {
    Players,
    Controls,
    Dices,
    PopupRule,
  },
  methods: {
    handleNewGame() {
      this.isOpenPopup = true;
    },
    handleConfirm() {
      this.isPlaying = true;
      this.isOpenPopup = false;
      this.activePlayer = 0;
      this.scoresPlayer = [0, 0];
      this.currentScore = 0;
      this.dices = [1, 1];
    },
    handleRollDice() {
      if (this.isPlaying) {
        //xoay xuc
        var dice1 = Math.floor(Math.random() * 6) + 1;
        var dice2 = Math.floor(Math.random() * 6) + 1;
        this.dices = [dice1, dice2];
        console.log(dice1, dice2);
      } else {
        alert("vui long click NewGame");
      }
    },
  },
};
</script>

<style>
* {
  margin: 0;
  padding: 0;
  box-sizing: border-box;
}

.clearfix::after {
  content: "";
  display: table;
  clear: both;
}

body {
  background-image: linear-gradient(
      rgba(62, 20, 20, 0.4),
      rgba(62, 20, 20, 0.4)
    ),
    url("/src/public/assets/back.jpg");
  background-size: cover;
  background-position: center;
  font-family: Lato;
  font-weight: 300;
  position: relative;
  height: 100vh;
  color: #555;
}

.wrapper {
  width: 1000px;
  position: absolute;
  top: 50%;
  left: 50%;
  transform: translate(-50%, -50%);
  background-color: #fff;
  box-shadow: 0px 10px 50px rgba(0, 0, 0, 0.3);
  overflow: hidden;
}
</style>
