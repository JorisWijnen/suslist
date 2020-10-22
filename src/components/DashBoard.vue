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
        <draggable class="draggable" :list="CrewmateList" group="people" @change="log">
          <div class="draggable-item" v-for="(item, index) in CrewmateList" :key="item.color">
            <Card :index="index" :image='item.image' :alive="item.alive" v-on:toggle="toggle1"/>
          </div>
        </draggable>
      </b-col>

      <b-col title="Not suspicous" style="background-color: #feff7f">
        <h3 class="column-title">Not suspicious</h3>
        <draggable class="draggable" :list="NotSuspiciousList" group="people" @change="log">
          <div class="draggable-item" v-for="(item, index) in NotSuspiciousList" :key="item.color">
            <Card :index="index" :image='item.image' :alive="item.alive" v-on:toggle="toggle2"/>
          </div>
        </draggable>
      </b-col>

      <b-col title="Neutral" style="background-color: #fadf7f;">
        <h3 class="column-title">Neutral</h3>
        <draggable class="draggable" :list="NeutralList" group="people" @change="log">
          <div class="draggable-item" v-for="(item, index) in NeutralList" :key="item.color">
            <Card :index="index" :image='item.image' :alive="item.alive" v-on:toggle="toggle3"/>
          </div>
        </draggable>
      </b-col>

      <b-col title="Suspicious" style="background-color: #f7bf7f;">
        <h3 class="column-title">Suspicious</h3>
        <draggable class="draggable" :list="SuspiciousList" group="people" @change="log">
          <div class="draggable-item" v-for="(item, index) in SuspiciousList" :key="item.color">
            <Card :index="index" :image='item.image' :alive="item.alive" v-on:toggle="toggle4"/>
          </div>
        </draggable>
      </b-col>

      <b-col title="Imposter" style="background-color: #f37e7f;">
        <h3 class="column-title">Imposter</h3>
        <draggable class="draggable" :list="ImposterList" group="people" @change="log">
          <div class="draggable-item" v-for="(item, index) in ImposterList" :key="item.color">
            <Card :index="index" :image='item.image' :alive="item.alive" v-on:toggle="toggle5"/>
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
          { color: "Black", image: "blackcrewpng.png", alive:true },
          { color: "Blue", image: "bluecrewpng.png", alive:true },
          { color: "Brown", image: "browncrewpng.png", alive:true },
          { color: "Cyan", image: "cyancrewpng.png", alive:true },
          { color: "Green", image: "greencrewpng.png", alive:true },
          { color: "Lime", image: "limecrewpng.png", alive:true },
          { color: "Orange", image: "orangecrewpng.png", alive:true },
          { color: "Pink", image: "pinkcrewpng.png", alive:true },
          { color: "Purple", image: "purplecrewpng.png", alive:true },
          { color: "Red", image: "redcrewpng.png", alive:true },
          { color: "White", image: "whitecrewpng.png", alive:true },
          { color: "Yellow", image: "yellowcrewpng.png", alive:true }
        ],
        SuspiciousList: [],
        ImposterList: []
      }
    },
    methods: {
      toggle1(index) {
        // Toggle alive status for element with color
        this.CrewmateList[index].alive = !this.CrewmateList[index].alive
      },
      toggle2(index) {
        // Toggle alive status for element with color
        this.NotSuspiciousList[index].alive = !this.NotSuspiciousList[index].alive
      },
      toggle3(index) {
        // Toggle alive status for element with color
        this.NeutralList[index].alive = !this.NeutralList[index].alive
      },
      toggle4(index) {
        // Toggle alive status for element with color
        this.SuspiciousList[index].alive = !this.SuspiciousList[index].alive
      },
      toggle5(index) {
        // Toggle alive status for element with color
        this.ImposterList[index].alive = !this.ImposterList[index].alive
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
  text-align: center;
}

.dashboard #header p {
  display: inline-block;
}

.dashboard #header #reset {
  position: relative;
  float: left;
}

.dashboard #header #github {
  position: relative;
  float: right;
}

.dashboard #table {
  height: 90%;
}
.dashboard #table .column-title {
  height: 5%;
}
.dashboard #table .draggable {
  height: 90%;
}

.dashboard #table .draggable-item {
  width: 50%;
  display: inline-block;
  float: left;
}
</style>
