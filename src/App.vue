<template>
  <div id="app">
    <Header />
    <div class="teams-container border-right">
      <Team
        v-for="(team, index) in teams"
        :key="index"
        :teamName="team.teamName"
        :score="team.score"
        :ronda="ronda"
        :missa="missa"
        :tringla="tringla"
        :pegar1="pegar1"
        :pegar2="pegar2"
        :pegar5="pegar5"
        :subtractPoint="subtractPoint"
        :updateTeamName="updateTeamName"
        :index="index"
      />
    </div>
    <Winner
      v-show="isWinnerModalVisible"
      :winningTeamName="winningTeamName"
      :resetGame="resetGame"
    />
    <div class="modal-overlay" v-show="isWinnerModalVisible"></div>
  </div>
</template>

<script>
import Header from './components/Header.vue'
import Team from './components/Team.vue'
import Winner from './components/Winner.vue'

export default {
  name: 'app',
  components: {
    Header,
    Team,
    Winner
  },
  data() {
    return {
      teams: [
        {
          teamName: 'Mamie',
          score: 0
        },
        {
          teamName: 'Joueur2',
          score: 0
        }
      ],
      newTeam: ''
    }
  },
  methods: {
    ronda(index) {
      this.teams[index].score++
    },
    missa(index) {
      this.teams[index].score++
    },
    tringla(index) {
      this.teams[index].score += 3;
    },
    pegar1(index) {
      this.teams[index].score++
    },
    pegar2(index) {
      this.teams[index].score += 2;
    },
    pegar5(index) {
      this.teams[index].score += 5;
    },
    subtractPoint(index) {
      if (this.teams[index].score > 0) this.teams[index].score--
    },
    createNewTeam() {
      this.teams.push({ teamName: this.newTeam, score: 0 })
      this.newTeam = ''
    },
    updateTeamName(newTeamName, index) {
      this.teams[index].teamName = newTeamName
    },
    resetGame() {
      this.teams.forEach(team => (team.score = 0))
    }
  },
  computed: {
    isWinnerModalVisible() {
      return this.teams.some(team => team.score > 20 )
    },
    winningTeamName() {
      let highestScore = 0
      this.teams.forEach(team =>
        team.score > highestScore ? (highestScore = team.score) : highestScore
      )
      return this.teams.find(team => team.score === highestScore).teamName
    }
  }
}
</script>

<style>
#app {
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
}

body {
  margin: 0;
}

.teams-container {
  margin-top: 3rem;
  display: flex;
  flex-direction: row;
  justify-content: space-around;
}

.new-team-wrapper {
  margin-top: 3rem;
  display: flex;
  flex-direction: row;
  justify-content: center;
}

.new-team-container {
  width: 30%;
}

.modal-overlay {
  position: fixed;
  top: 0;
  left: 0;
  width: 100%;
  height: 100%;
  background-color: rgba(200, 200, 200, 0.7);
  z-index: 9;
}
</style>
