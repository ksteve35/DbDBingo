<template>
  <div class="center">
    <b-row v-for="i in 5" :key="i">
      <b-col
        v-for="j in 5"
        :key="j"
        :id="calculateID(i - 1, j - 1)"
        :class="'square ' + (calculateID(i - 1, j - 1) == 'cell12' ? 'enabled' : 'disabled')"
        @click="swapCellColor($event)"
      >
        ID {{ `${i}${j}` }}
        {{calculateID(i - 1, j - 1)}}
      </b-col>
    </b-row>
  </div>
</template>

<style scoped>
.center {
  margin: auto;
  max-width: 30vw;
  min-width: 410px;
}
.disabled {
  background-color: rgb(64, 64, 64);
}
.enabled {
  background-color: rgb(99, 0, 0);
}
.square {
  border: 1px solid black;
  height: 0;
  padding-bottom: 20%;
  text-align: center;

  /* Avoids "double borders" */
  margin-top: -1px;
  margin-left: -1px;
}
</style>

<script>
import {regenerateNonToxicChallenges} from '../scripts/challengeScripts.js'

export default {
  name: 'BingoSheet',
  data() {
    return {
      challenges: [],
      displayedChallenges: []
    }
  },
  methods: {
    calculateID(row, col) {
      let id = 0 + (col * 0)

      switch (row) {
        case 0:
        case 1:
          id += 0
          break
        case 2:
        case 3:
          id += 10
          break
        case 4:
          id += 20
          break
      }

      id += row % 2 == 0 ? col : col + 5

      return `cell${id}`
    },
    getChallenges() {
      this.challenges = this.regenerateNonToxicChallenges()
      let newDisplayChallenges = []
      for (let i in this.challenges) {
        newDisplayChallenges.push({
            id: parseInt(i),
            challenge: this.challenges[i]
        })
      }
      // Shuffles the array
      newDisplayChallenges.sort(() => Math.random() - 0.5)
      this.displayedChallenges = [...newDisplayChallenges].slice(0, 24)
    },
    getRandomNumber(high) {
      // Returns a random integer between 0 and (high - 1)
      return Math.floor(Math.random() * high)
    },
    getRandomSurvivorBloodpointCategory() {
      // Returns Objective, Survival, Altruism, or Boldness
      let category = ''
      switch (this.getRandomNumber(4)) {
        case 0:
          category = 'Objective'
          break
        case 1:
          category = 'Survival'
          break
        case 2:
          category = 'Altruism'
          break
        case 3:
          category = 'Boldness'
          break
      }
      return category
    },
    regenerateNonToxicChallenges,
    swapCellColor(evt) {
      let id = evt.target.id
      let ele = document.getElementById(id)

      // Check that id is not the center cell (33)
      if (id != 'cell12') {
        if (ele.classList.contains('disabled')) {
          ele.classList.replace('disabled', 'enabled')
        } else {
          ele.classList.replace('enabled', 'disabled')
        }
      }
    }
  },
  mounted() {
    this.getChallenges()
  }
}
</script>
