<template>
  <div>
    <div>
      <h1 class="name">{{ teamName }}</h1>
      <p>Modifier le Nom</p>
      <b-form-input
        v-model="newTeamName"
        @keyup="updateTeamName(newTeamName, index)"
      />
      <p class="score display-2">{{ score }}</p>
      <div class="mb-4">
        <input v-model.number="marque" type="number" />
        <b-button
          class="btn-outline-warning ml-2"
          @click="addPoints(index, marque)"
        >
          Marquer
        </b-button>
      </div>
      <b-button
        class="btn btn-block mb-2 btn-outline-warning"
        @click="addPoints(index, 1)"
        >Ronda</b-button
      >
      <b-button
        class="btn btn-block mb-2 btn-outline-warning"
        @click="addPoints(index, 3)"
        >Tringla</b-button
      >
      <b-button
        class="btn btn-block mb-2 btn-outline-warning"
        @click="addPoints(index, 1)"
        >Missa</b-button
      >
      <b-button
        class="btn btn-block mb-2 btn-outline-warning"
        @click="addPoints(index, 1)"
        >Taper 1</b-button
      >
      <b-button
        class="btn btn-block mb-2 btn-outline-warning"
        @click="addPoints(index, 2)"
        >Taper 2</b-button
      >
      <b-button
        class="btn btn-block mb-2 btn-outline-warning"
        @click="addPoints(index, 5)"
        >Taper 5</b-button
      >
    </div>
    <b-button
      class="btn btn-block mb-2 btn-outline-danger btn-lg"
      @click="subtractPoint(index)"
      >Enlever 1 Point</b-button
    >
  </div>
</template>

<script>
export default {
  name: "Team",
  props: {
    teamName: String,
    score: Number,
    index: Number,
    addPoints: Function,
    subtractPoint: Function,
    updateTeamName: Function
  },
  data() {
    return {
      newTeamName: this.teamName,
      marque: 0
    };
  }
};
</script>

<style scoped>
.score {
  margin-top: 1rem;
  font-size: 2.5rem;
  color: #f6e056;
}
.name {
  color: #f6e056;
}
</style>
