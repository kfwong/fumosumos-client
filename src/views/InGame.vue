<template>
<div class="center-vertical" id="in-game">
    <div class="in-game-header">
        <h1>Game in Progress</h1>
        <!-- <span>Follow the instructions on the screen</span> -->
    </div>
    <img class="game-icon" src="@/assets/in-game/game1.gif">
    <div class="in-game-footer">
        Flap those flabby arms, and don't fall!
    </div>
</div>
</template>

<style lang="scss" scoped>
.in-game-header {
  font-size: 18px;
  margin-top: 10%;
  margin-bottom: 10%;
  text-align: center;
}

.in-game-footer {
  margin-top: 10%;
}

.game-icon {
  max-width: 80%;
}
</style>