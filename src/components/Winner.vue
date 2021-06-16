<template>
  <div>
    <h1>Bravo!</h1>
    <p>{{ winningTeamName }} a gagné la partie!</p>
    <b-button @click="resetGame">Recommencer</b-button>
  </div>
</template>

<script>
export default {
  name: 'Winner',
  props: {
    winningTeamName: String,
    resetGame: Function
  }
}
</script>

<style scoped>
div {
  background-color: #eee;
  position: fixed;
  top: 50%;
  left: 50%;
  transform: translate(-50%, -50%);
  z-index: 10;
  height: 350px;
  width: 550px;
  border: 1px solid grey;
  border-radius: 4px;
  display: flex;
  flex-direction: column;
  justify-content: center;
  align-items: center;
}
</style>
