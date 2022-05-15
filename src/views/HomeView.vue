<template>
  <div class="home">
    <Section3Vue />
<!--    <SecondVue />-->
<!--    <img alt="Vue logo" src="../assets/logo.png">-->
<!--    <HelloWorld msg="Welcome to Your Vue.js App"/>-->
  </div>
</template>

<script>
// @ is an alias to /src
// import HelloWorld from '@/components/HelloWorld.vue'
// import SecondVue from '@/components/SecondVue'
import Section3Vue from '@/components/Section3Vue'

export default {
  name: 'HomeView',
  components: {
    // HelloWorld,
    // SecondVue
    Section3Vue
  }
}
</script>
