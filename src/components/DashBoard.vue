<template>
    <b-container fluid class="dashboard" style="background-color: #fadf7f;">
    <b-row id="header" align-h="center">
      <img class="icon" src="../assets/icon.png"/>
      <h1> Among Us Suspicion Table </h1>
      <img class="icon" src="../assets/icon.png"/>
    </b-row>
      <b-row id="table">
        <b-col title="Crewmate" style="background-color: #bfff7f;">
          <h3 class="column-title">Crewmate</h3>
          <draggable class="list-group draggable" :list="CrewmateList" group="people" @change="log">
            <div class="draggable-item" v-for="item in CrewmateList" :key="item.color">
              <Card :image='item.image'/>
            </div>
          </draggable>
        </b-col>

        <b-col title="Not suspicous" style="background-color: #feff7f">
          <h3 class="column-title">Not suspicious</h3>
          <draggable class="list-group draggable" :list="NotSuspiciousList" group="people" @change="log">
            <div class="draggable-item" v-for="item in NotSuspiciousList" :key="item.color">
              <Card :image='item.image'/>
            </div>
          </draggable>
        </b-col>

        <b-col title="Neutral" style="background-color: #fadf7f;">
          <h3 class="column-title">Neutral</h3>
          <draggable class="list-group draggable" :list="NeutralList" group="people" @change="log">
            <div class="draggable-item" v-for="item in NeutralList" :key="item.color">
              <Card :image='item.image'/>
            </div>
          </draggable>
        </b-col>

        <b-col title="Suspicious" style="background-color: #f7bf7f;">
          <h3 class="column-title">Suspicious</h3>
          <draggable class="list-group draggable" :list="SuspiciousList" group="people" @change="log">
            <div class="draggable-item" v-for="item in SuspiciousList" :key="item.color">
              <Card :image='item.image'/>
            </div>
          </draggable>
        </b-col>

        <b-col title="Imposter" style="background-color: #f37e7f;">
          <h3 class="column-title">Imposter</h3>
          <draggable class="list-group draggable" :list="ImposterList" group="people" @change="log">
            <div class="draggable-item" v-for="item in ImposterList" :key="item.color">
              <Card :image='item.image'/>
            </div>
          </draggable>
        </b-col>
      </b-row>
    </b-container>
</template>


<script>
import Card from './Card.vue'
 import draggable from 'vuedraggable'

export default {
    name: "DashBoard",
    components: {
      Card,
      draggable
    },
    data() {
      return {
        CrewmateList: [],
        NotSuspiciousList: [],
        NeutralList: [
          { color: "Black", image: "blackcrewpng.png" },
          { color: "Blue", image: "bluecrewpng.png" },
          { color: "Brown", image: "browncrewpng.png" },
          { color: "Cyan", image: "cyancrewpng.png" },
          { color: "Green", image: "greencrewpng.png" },
          { color: "Lime", image: "limecrewpng.png" },
          { color: "Orange", image: "orangecrewpng.png" },
          { color: "Pink", image: "pinkcrewpng.png" },
          { color: "Purple", image: "purplecrewpng.png" },
          { color: "Red", image: "redcrewpng.png" },
          { color: "White", image: "whitecrewpng.png" },
          { color: "Yellow", image: "yellowcrewpng.png" }
        ],
        SuspiciousList: [],
        ImposterList: []
      }
    }
  }
</script>

<style lang="css">
.icon {
  width: 40px;
  height: 40px;
}
.dashboard {
  background-color: white;
  height: 100%;
}
.dashboard #header {
  height:10%;
}

.dashboard #header h1 {
  margin-left: 20px;
  margin-right: 20px;
}

.dashboard #header #github {
  height: 40px
}

.dashboard #table {
  height: 90%;
}
.dashboard #table .column-title {
  height: 5%;
}
.dashboard #table .draggable {
  height: 90%;
  display: inline-block;
}

.dashboard #table .draggable-item {
  width: 50%;
  display: inline-block;
  float: left;
}
</style>
