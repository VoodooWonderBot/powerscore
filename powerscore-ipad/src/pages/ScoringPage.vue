<script setup lang="ts">

import NewGoal from 'components/TabletUI/NewGoal.vue';
import NewPenalty from 'components/TabletUI/NewPenalty.vue';
import TeamCard from 'components/TabletUI/TeamCard.vue';
import Timer from 'components/TabletUI/TimerMain.vue';
import { reactive } from 'vue'

// TODO: Swap this out for real data, integrate with powerplay api.
// TODO: State management?
const dummyData = reactive({
  teamOne: {
    name: 'Trash Pandas',
    logo: 'pathToLogoPlaceholder',
  },
  teamTwo: {
    name: 'Garbage Gators',
    logo: 'pathToLogoPlaceholder',
  },
})
</script>

<template>
  <!--  NOTE: just trying to get a basic structure here to split up the work a bit, we can make it prettier and move/fine tune things as we go -->
  <div id="score-keeper-root" class="q-pa-md root-width q-mx-auto">
    <h1 class="q-pa-md header text-center">Penalty & Goal Tracker</h1>

    <!--    Teams     -->
    <div class="row">
      <TeamCard :team-name="dummyData.teamOne.name" :home-team="true" class="col"/>
      <TeamCard :team-name="dummyData.teamTwo.name" :home-team="false" class="col"/>
    </div>

    <!-- Timer (and period)  -->
    <div class="row justify-center">
      <Timer/>
    </div>
    <div class="row justify-center">
<!--        Manual button to add penalty TODO: Also create an event listener that will pop this up when the rink signals a penalty -->
        <NewPenalty></NewPenalty>
<!--        Manual button to add goal TODO: Also create an event listener that will pop this up when the rink signals a score -->
        <NewGoal></NewGoal>
    </div>
  </div>
</template>

<style scoped>
.header {
  font-size: 1.125rem; /* 18px */
  line-height: 1.75rem; /* 28px */
}

.root-width {
  max-width: 1000px;
}
</style>
