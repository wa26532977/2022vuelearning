<template>
<div>
  <h1>{{welcome}}</h1>
  <h3>My course goals</h3>
  <input type="text" v-model="goal" @keyup.enter="addGoal">
  <button @click="addGoal">Add Goal</button>
  <p v-if="goals.length === 0">No goals have been added yet-please start adding some</p>
  <ul v-else>
    <li v-for="(g, index) in goals" :key="index">
      {{g}}
    </li>
  </ul>
</div>
</template>

<script>
export default {
  name: 'Section3Vue',
  data () {
    return {
      welcome: 'welcome to section 3',
      goals: [],
      goal: ''
    }
  },
  methods: {
    addGoal () {
      this.goals.push(this.goal)
      this.goal = ''
    }
  }
}
</script>

<style scoped>

</style>
