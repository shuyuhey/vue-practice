<template>
  <div id="app">
    <h1>Talens</h1>
    <div class="talent-cards-container">
      <div class="talent-card-container" v-for="talent in talents" v-bind:key="talent.name">
        <TalentCard v-bind:talent="talent"/>
      </div>
    </div>
  </div>
</template>

<script lang="ts">
import { Component, Vue } from "vue-property-decorator";
import HelloWorld from "./components/HelloWorld.vue";
import TalentCard from "./components/TalentCard.vue";
import faker from "faker";
import Talent from "./models/talent";

const colors = [
  "#1abc9c",
  "#2ecc71",
  "#3498db",
  "#9b59b6",
  "#34495e",
  "#f1c40f",
  "#e67e22",
  "#e74c3c"
];

let talents: Talent[] = [...new Array(30)].map(
  (_, index) =>
    new Talent(
      faker.name.findName(),
      faker.lorem.paragraph(),
      faker.image.avatar(),
      colors[index % colors.length]
    )
);

@Component({
  components: {
    HelloWorld,
    TalentCard
  }
})
export default class App extends Vue {
  talents: Talent[] = talents;
}
</script>

<style>
#app {
  font-family: "Avenir", Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}

.talent-cards-container {
  margin: 0 auto;
  display: flex;
  flex-wrap: wrap;
  justify-content: center;
}

.talent-card-container {
  margin: 10px;
}
</style>
