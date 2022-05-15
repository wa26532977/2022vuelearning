<template>
  <div>
    <h1>{{welcome}}</h1>
    <h2>Dynamic css styling</h2>
<!--  override all other css  -->
    <button class="demo" @click="boxChanged(0)" :style="{borderColor: boxState[0] ? 'red' : '#ccc'}">boxA</button>
    <button class="demo" @click="boxChanged(1)" :style="{borderColor: boxState[1] ? 'red' : '#ccc'}">boxB</button>
    <button class="demo" @click="boxChanged(2)" :style="{borderColor: boxState[2] ? 'red' : '#ccc'}">boxC</button>
    <h2>Dynamic css class</h2>
    <button :class="{demo: true, active: boxState[0]}" @click="boxChanged(0)">boxA</button>
    <button class='demo' :class="{active:boxState[1]}" @click="boxChanged(1)">boxB</button>
    <button :class="boxAClasses" @click="boxChanged(2)">boxC</button>
    <p>learn more <a :href="vueLink">{{ Math.random() > 0.5 ? "about Vue" : "Master Vue" }}</a></p>
    <p v-html="vueHtml" />
    <h2>Events in Actions</h2>
    <button @click="eventCounter++">Add</button>
    <button @click="reduceCounter(2)"  @click.middle="reduceCounter(1)">Reduce</button>
    <p v-once>Starting Counter: {{eventCounter}}</p>
    <p>Result: {{eventCounter}}</p>
    <!--  v-model for two-way binding replace :value and @input -->
    <!--    <input type="text" :value="name" @input="setName($event, ' Wang')" v-on:keyup.enter="confirmName=name">-->
    <input type="text" v-model="name" @keyup.enter="confirmName = name">
    <input type="text" v-model="lastName" @keyup.enter="confirmName = lastName">
    <!--  this function will run everything anything update in our dom  -->
    <p>from output full name: {{outputFullname()}}</p>
    <!--  following computed properties will only update if the variable inside updates  -->
    <p>computed properties: {{outputFullNameComputed}}</p>
    <!--  fullName is under watch  -->
    <p>watch the name data variable if name changes, the full name changes too, full name: {{fullName}}</p>
    <p>Your confirm Name: {{confirmName}}</p>
    <button @click="resetName">Reset Input</button>
    <form action="" @submit.prevent="submitForm">
      <input type="text">
      <button>Sign up</button>
    </form>
  </div>
</template>

<script>
export default {
  name: 'SecondVue',
  data () {
    return {
      boxState: [false, false, false],
      welcome: 'this is from second vue',
      vueLink: 'https://vuejs.org',
      vueHtml: '<h1>this is good html code</h1>',
      eventCounter: 0,
      name: '',
      confirmName: '',
      fullName: '',
      lastName: ''
    }
  },
  methods: {
    boxChanged (boxNum) {
      this.boxState[boxNum] = !this.boxState[boxNum]
    },
    outputFullname () {
      console.log('methods')
      if (this.name === '') {
        return ''
      }
      return this.name + ' ' + 'wang'
    },
    resetName () {
      this.name = ''
      this.confirmName = ''
    },
    submitForm () {
      // event.preventDefault()
      console.log('form submitted')
    },
    setName (event, lastName) {
      // console.log(event.target.value)
      this.name = event.target.value
    },
    outputGoal () {
      const randomNum = Math.random()
      if (randomNum < 0.5) {
        return 'learn vue'
      } else {
        return 'Master vue!'
      }
    },
    reduceCounter (num) {
      this.eventCounter -= num
    }
  },
  computed: {
    outputFullNameComputed () {
      console.log('computed')
      return this.name + ' ' + this.lastName
    },
    boxAClasses () {
      return { active: this.boxState[2] }
    }
  },
  watch: {
    // watch, watch is the certain data name, will run the method if the data name is changed.
    name (newValue, oldValue) {
      console.log('from watch')
      this.fullName = newValue + ' ' + this.lastName
    },
    eventCounter (newValue) {
      if (newValue > 10) {
        this.eventCounter = 0
      }
    }
  }
}
</script>

<style scoped>
.active {
  border-color: red;
  background-color: salmon;
}

</style>
