<template>
    <b-container fluid class="dashboard" style="background-color: #fadf7f;">
    <b-row id="header" align-v="center">
      <b-col>
        <b-button id="reset" variant="dark" v-on:click="reset">Reset Board</b-button>
      </b-col>
      <b-col cols="2">
        <!-- Placeholder to center title -->
      </b-col>
      <b-col cols='4'>
        <h1> Among Us Suspicion List </h1>
        <p>- Drag and drop characters to the separate columns.</p>
        <p>- Click on a character to toggle their alive status. </p>
        <p>- Drag a character to the trashcan to remove them from the board.</p>
      </b-col>
      <b-col cols="2" title="trashcan">
        <draggable class="list-group draggable" group="characters">
        </draggable>
      </b-col>
      <b-col>
        <b-button id="github" variant="dark" target="_blank" href="https://github.com/JorisWijnen/suslist">GitHub Project</b-button>
      </b-col>
    </b-row>
    <b-row id="body">
      <b-col title="Crewmate" style="background-color: #bfff7f;">
        <draggable class="list-group draggable" :list="CrewmateList" group="characters" draggable=".draggable-item">
          <h3 slot="header" class="column-title">Crewmate</h3>
          <div class="draggable-item" v-for="(item, index) in CrewmateList" :key="item.color">
            <Card :index="index" :image='item.image' :dead_image='item.dead_image' :alive="item.alive" v-on:toggle="toggle1"/>
          </div>
        </draggable>
      </b-col>

      <b-col title="Not suspicous" style="background-color: #feff7f">
        <draggable class="list-group draggable" :list="NotSuspiciousList" group="characters" draggable=".draggable-item">
          <h3 slot="header" class="column-title">Not suspicious</h3>
          <div class="draggable-item" v-for="(item, index) in NotSuspiciousList" :key="item.color">
            <Card :index="index" :image='item.image' :dead_image='item.dead_image' :alive="item.alive" v-on:toggle="toggle2"/>
          </div>
        </draggable>
      </b-col>

      <b-col title="Neutral" style="background-color: #fadf7f;">
        <draggable class="list-group draggable" :list="NeutralList" group="characters" draggable=".draggable-item">
          <h3 slot="header" class="column-title">Neutral</h3>
          <div class="draggable-item" v-for="(item, index) in NeutralList" :key="item.color">
            <Card :index="index" :image='item.image' :dead_image='item.dead_image' :alive="item.alive" v-on:toggle="toggle3"/>
          </div>
        </draggable>
      </b-col>

      <b-col title="Suspicious" style="background-color: #f7bf7f;">
        <draggable class="list-group draggable" :list="SuspiciousList" group="characters" draggable=".draggable-item">
          <h3 slot="header" class="column-title">Suspicious</h3>
          <div class="draggable-item" v-for="(item, index) in SuspiciousList" :key="item.color">
            <Card :index="index" :image='item.image' :dead_image='item.dead_image' :alive="item.alive" v-on:toggle="toggle4"/>
          </div>
        </draggable>
      </b-col>

      <b-col title="Imposter" style="background-color: #f37e7f;">
        <draggable class="list-group draggable" :list="ImposterList" group="characters" draggable=".draggable-item">
          <h3 slot="header" class="column-title">Imposter</h3>
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
          { color: "Black", image: "black.png", dead_image: "black-dead.png", alive:true },
          { color: "Blue", image: "blue.png", dead_image: "blue-dead.png", alive:true },
          { color: "Brown", image: "brown.png", dead_image: "brown-dead.png", alive:true },
          { color: "Cyan", image: "cyan.png", dead_image: "cyan-dead.png", alive:true },
          { color: "Green", image: "green.png", dead_image: "green-dead.png", alive:true },
          { color: "Lime", image: "lime.png", dead_image: "lime-dead.png", alive:true },
          { color: "Orange", image: "orange.png", dead_image: "orange-dead.png", alive:true },
          { color: "Pink", image: "pink.png", dead_image: "pink-dead.png", alive:true },
          { color: "Purple", image: "purple.png", dead_image: "purple-dead.png", alive:true },
          { color: "Red", image: "red.png", dead_image: "red-dead.png", alive:true },
          { color: "White", image: "white.png", dead_image: "white-dead.png", alive:true },
          { color: "Yellow", image: "maroon.png", dead_image: "maroon-dead.png", alive:true },
          { color: "Yellow", image: "rose.png", dead_image: "rose-dead.png", alive:true },
          { color: "Yellow", image: "banana.png", dead_image: "banana-dead.png", alive:true },
          { color: "Yellow", image: "gray.png", dead_image: "gray-dead.png", alive:true },
          { color: "Yellow", image: "tan.png", dead_image: "tan-dead.png", alive:true },
          { color: "Yellow", image: "coral.png", dead_image: "coral-dead.png", alive:true },
          { color: "Yellow", image: "fortegreen.png", dead_image: "fortegreen-dead.png", alive:true },
          { color: "Yellow", image: "olive.png", dead_image: "olive-dead.png", alive:true }
        ],
        SuspiciousList: [],
        ImposterList: [],
        TrashcanList: []
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
        this.CrewmateList = []; this.NotSuspiciousList = []; this.SuspiciousList = []; this.ImposterList = []; this.TrashcanList = [];
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
  min-height:20vh;
  text-align: center;
}

.dashboard #header h1, .dashboard #header p {
  display: block;
}

.dashboard #header .draggable {
  align-items: center;
  min-height: 125px;
  background-image: url('../assets/trashcan.png');
  background-size: contain;
  background-repeat: no-repeat;
  background-position: center;
}

.dashboard #header .draggable-item {
  height: 75%;
  width: 75%;
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
  min-height: 80vh;
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
