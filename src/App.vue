<template>
  <main class="columns is-gapless is-multiline" :class="{'dark-mode': darkModeOn}">
    <div class="column is-one-quarter">
      <SideBar @changeTheme="changeTheme"/>
    </div>
    <div class="column is-three-quarter content">
      <FormCreate @onSaveActivity="saveActivity" />
      <div class="list">
        <ActivityCard v-for="(activity, index) in activities" :key="index" :activity="activity" />
        <BoxActivity v-if="emptyList"> Você não está muito produtivo hoje, considere a possibilidade de fazer mais tarefas.</BoxActivity>
      </div>
    </div>
  </main>
</template>

<script lang="ts">
import { defineComponent } from 'vue'
import SideBar from '@/components/SideBar.vue';
import FormCreate from "./components/FormCreate.vue"
import ActivityCard from "./components/ActivityCard.vue"
import IActivity from "./Interfaces/IActivity";
import BoxActivity from "./components/BoxActivity.vue";
export default defineComponent({
  name: 'App',
  components: {
    SideBar,
    FormCreate,
    ActivityCard,
    BoxActivity
  },
  data() {
    return {
      activities: [] as IActivity[],
      darkModeOn: false,
    }
  },
  computed:{
    emptyList() :boolean{
      return this.activities.length === 0
    },
  },
  methods: {
    saveActivity(activities: IActivity) {
      this.activities.push(activities)
    },
    changeTheme(darkModeOn: boolean){
      this.darkModeOn = darkModeOn;
    }
  },
});
</script>

<style>
.list {
  padding: 1.25rem;
}
main{
  --bg-primary: #f8f5f5;
  --Text-primary: #000;
}
main.dark-mode{
  --bg-primary: #2b2d42;
  --Text-primary: #ddd;
}
.content{
background-color: var(--bg-primary);
}
</style>
