<template>
    <b-container fluid class="dashboard" style="background-color: #fadf7f;">
    <b-row id="header" align-v="center">
      <b-col>
        <b-button id="reset" variant="dark" v-on:click="reset">Reset Board</b-button>
      </b-col>
      <b-col cols='6'>
        <h1> Among Us Suspicion List</h1>
        <p>Drag and drop characters to the separate columns. Click on a character to toggle their alive status.</p>
      </b-col>
      <b-col>
        <b-button id="github" variant="dark" target="_blank" href="https://github.com/JorisWijnen/suslist">GitHub Project</b-button>
      </b-col>
    </b-row>
    <b-row id="body">
      <b-col title="Crewmate" style="background-color: #bfff7f;">
        <h3 class="column-title">Crewmate</h3>
        <draggable class="list-group draggable" :list="CrewmateList" group="characters" :options="{delay:100}">
          <div class="draggable-item" v-for="(item, index) in CrewmateList" :key="item.color">
            <Card :index="index" :image='item.image' :dead_image='item.dead_image' :alive="item.alive" v-on:toggle="toggle1"/>
          </div>
        </draggable>
      </b-col>

      <b-col title="Not suspicous" style="background-color: #feff7f">
        <h3 class="column-title">Not suspicious</h3>
        <draggable class="list-group draggable" :list="NotSuspiciousList" group="characters" {delay:100}>
          <div class="draggable-item" v-for="(item, index) in NotSuspiciousList" :key="item.color">
            <Card :index="index" :image='item.image' :dead_image='item.dead_image' :alive="item.alive" v-on:toggle="toggle2"/>
          </div>
        </draggable>
      </b-col>

      <b-col title="Neutral" style="background-color: #fadf7f;">
        <h3 class="column-title">Neutral</h3>
        <draggable class="list-group draggable" :list="NeutralList" group="characters" {delay:100}>
          <div class="draggable-item" v-for="(item, index) in NeutralList" :key="item.color">
            <Card :index="index" :image='item.image' :dead_image='item.dead_image' :alive="item.alive" v-on:toggle="toggle3"/>
          </div>
        </draggable>
      </b-col>

      <b-col title="Suspicious" style="background-color: #f7bf7f;">
        <h3 class="column-title">Suspicious</h3>
        <draggable class="list-group draggable" :list="SuspiciousList" group="characters" {delay:100}>
          <div class="draggable-item" v-for="(item, index) in SuspiciousList" :key="item.color">
            <Card :index="index" :image='item.image' :dead_image='item.dead_image' :alive="item.alive" v-on:toggle="toggle4"/>
          </div>
        </draggable>
      </b-col>

      <b-col title="Imposter" style="background-color: #f37e7f;">
        <h3 class="column-title">Imposter</h3>
        <draggable class="list-group draggable" :list="ImposterList" group="characters" {delay:100}>
          <div class="draggable-item" v-for="(item, index) in ImposterList" :key="item.color">
            <Card :index="index" :image='item.image' :dead_image='item.dead_image' :alive="item.alive" v-on:toggle="toggle5"/>
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
    name: "DashBoardMobile",
    components: {
      Card,
      draggable
    },
    data() {
      return {
        CrewmateList: [],
        NotSuspiciousList: [],
        NeutralList: [
          { color: "Black", image: "blackcrewpng.png", dead_image: "blackcrewpng-dead.png", alive:true },
          { color: "Blue", image: "bluecrewpng.png", dead_image: "bluecrewpng-dead.png", alive:true },
          { color: "Brown", image: "browncrewpng.png", dead_image: "browncrewpng-dead.png", alive:true },
          { color: "Cyan", image: "cyancrewpng.png", dead_image: "cyancrewpng-dead.png", alive:true },
          { color: "Green", image: "greencrewpng.png", dead_image: "greencrewpng-dead.png", alive:true },
          { color: "Lime", image: "limecrewpng.png", dead_image: "limecrewpng-dead.png", alive:true },
          { color: "Orange", image: "orangecrewpng.png", dead_image: "orangecrewpng-dead.png", alive:true },
          { color: "Pink", image: "pinkcrewpng.png", dead_image: "pinkcrewpng-dead.png", alive:true },
          { color: "Purple", image: "purplecrewpng.png", dead_image: "purplecrewpng-dead.png", alive:true },
          { color: "Red", image: "redcrewpng.png", dead_image: "redcrewpng-dead.png", alive:true },
          { color: "White", image: "whitecrewpng.png", dead_image: "whitecrewpng-dead.png", alive:true },
          { color: "Yellow", image: "yellowcrewpng.png", dead_image: "yellowcrewpng-dead.png", alive:true }
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
      },
      reset() {
        this.CrewmateList = []; this.NotSuspiciousList = []; this.SuspiciousList = []; this.ImposterList = [];
        this.NeutralList = [
          { color: "Black", image: "blackcrewpng.png", dead_image: "blackcrewpng-dead.png", alive:true },
          { color: "Blue", image: "bluecrewpng.png", dead_image: "bluecrewpng-dead.png", alive:true },
          { color: "Brown", image: "browncrewpng.png", dead_image: "browncrewpng-dead.png", alive:true },
          { color: "Cyan", image: "cyancrewpng.png", dead_image: "cyancrewpng-dead.png", alive:true },
          { color: "Green", image: "greencrewpng.png", dead_image: "greencrewpng-dead.png", alive:true },
          { color: "Lime", image: "limecrewpng.png", dead_image: "limecrewpng-dead.png", alive:true },
          { color: "Orange", image: "orangecrewpng.png", dead_image: "orangecrewpng-dead.png", alive:true },
          { color: "Pink", image: "pinkcrewpng.png", dead_image: "pinkcrewpng-dead.png", alive:true },
          { color: "Purple", image: "purplecrewpng.png", dead_image: "purplecrewpng-dead.png", alive:true },
          { color: "Red", image: "redcrewpng.png", dead_image: "redcrewpng-dead.png", alive:true },
          { color: "White", image: "whitecrewpng.png", dead_image: "whitecrewpng-dead.png", alive:true },
          { color: "Yellow", image: "yellowcrewpng.png", dead_image: "yellowcrewpng-dead.png", alive:true }
        ];
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
  min-height:10%;
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

.dashboard #body {
  min-height: 90%;
}
.dashboard #body .column-title {
  min-height: 5%;
}
.dashboard #body .draggable {
  min-height: 90%;
  display: block;
}

.dashboard #body .draggable-item {
  width: 50%;
  display: inline-block;
  float: left;
}
</style>
