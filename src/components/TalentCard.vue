<template>
  <div class="talent-box">
    <div class="cover-container" v-bind:style="{ background: talent.color }"></div>
    <div class="icon-container">
      <img v-bind:src="talent.image" alt>
    </div>
    <div class="profile-container">
      <div class="name">{{ talent.name }}</div>
      <div class="profile">{{ talent.profile }}</div>
    </div>
  </div>
</template>

<script lang="ts">
import { Component, Vue } from "vue-property-decorator";

import Talent from "@/models/talent";

type Data = {};

@Component({
  props: {
    talent: {
      type: Talent,
      required: true
    }
  }
})
export default class TalentCard extends Vue {
  bookmarked: boolean = false;
}
</script>

<style scoped>
.talent-box {
  width: 320px;
  height: 500px;
  box-shadow: #bdc3c7 1px 1px 30px 1px;
  border-radius: 8px;

  display: flex;
  flex-direction: column;
  position: relative;
  overflow: hidden;
}
.cover-container {
  width: 100%;
  height: 30%;
}

.icon-container {
  width: 100px;
  height: 100px;
  border-radius: 50px;
  overflow: hidden;
  object-fit: cover;

  position: absolute;
  top: calc(30% - 50px);
  left: calc(50% - 50px);

  background: #ecf0f1;
}

.icon-container img {
  width: 100%;
  height: 100%;
}

.profile-container {
  flex: 1;
  padding: 70px 20px 20px;
}

.name {
  font-weight: bold;
}

.profile {
  margin-top: 10px;
}
</style>


