<template>
  <div>
    <div>
      <h1>{{ teamName }}</h1>
      <p>Modifier le Nom</p>
      <b-form-input
        v-model="newTeamName"
        @keyup="updateTeamName(newTeamName, index)"
      />
      <p class="score">{{ score }}</p>
      <b-button class="btn btn-block mb-2" variant="success" @click="ronda(index)"
        >Ronda</b-button
      >
      <b-button class="btn btn-block mb-2" variant="success" @click="tringla(index)"
        >Tringla</b-button
      >
      <b-button class="btn btn-block mb-2" variant="success" @click="missa(index)"
        >Missa</b-button
      >
      <b-button class="btn btn-block mb-2" variant="success" @click="pegar1(index)"
        >Taper 1</b-button
      >
      <b-button class="btn btn-block mb-2" variant="success" @click="pegar2(index)"
        >Taper 2</b-button
      >
      <b-button class="btn btn-block mb-2" variant="success" @click="pegar5(index)"
        >Taper 5</b-button
      >
    </div>
    <b-button class="btn btn-block mb-2" variant="danger" @click="subtractPoint(index)"
      >Enlever 1 Point</b-button
    >
  </div>
</template>

<script>
export default {
  name: 'Team',
  props: {
    teamName: String,
    score: Number,
    ronda: Function,
    missa: Function,
    tringla: Function,
    pegar1: Function,
    pegar2: Function,
    pegar5: Function,
    subtractPoint: Function,
    updateTeamName: Function,
    index: Number
  },
  data() {
    return {
      newTeamName: this.teamName
    }
  }
}
</script>

<style scoped>
.score {
  margin-top: 1rem;
  font-size: 1.5rem;
}
</style>
