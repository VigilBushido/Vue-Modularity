<template>
  <div id="app">
    <!--<Greeting greeting="Hi" who="Everyone" /> -->

    <!-- using dynamic props with data binding -->
    <!--     <Hello greeting="Hello" v-bind:who="appWho" />
    <button @click="setWho('JavaScript')">JavaScript</button>
    <button @click="setWho('Everyone')">Everyone</button> -->

    <Greeting :greeting="greeting" :who="who" />
    <button @click="newGreeting()">New Greeting</button>
  </div>
</template>

<script>
import Greeting from "./components/Greeting";
//import Hello from "./components/Hello"; // using dynamic props with data binding

//imports for passing props that change over time
const possibleGreetings = [
  { greeting: "Hello", who: "Vue.js" },
  { greeting: "Hey", who: "Everyone" },
  { greeting: "Hi", who: "JavaScript" },
];
// components export
export default {
  name: "App",
  components: {
    Greeting,
    //Hello,
  },
  data() {
    return {
      //appWho: "Vue.js", // using dynamic props with data binding
      //4.02 below we make a greeting app
      /*    greeting: "Hello",
      who: "Vue.js",   // we refactor this so it only holds default index*/
      currentIndex: 0,
    };
  },
  computed: {
    // this is the intermediary computer propperty
    currentGreeting() {
      return possibleGreetings[this.currentIndex];
    },
    greeting() {
      return this.currentGreeting.greeting;
    },
    who() {
      return this.currentGreeting.who;
    },
  },
  methods: {
    newGreeting() {
      console.log(possibleGreetings.length - 1);
      this.currentIndex =
        this.currentIndex === possibleGreetings.length - 1
          ? 0
          : this.currentIndex + 1;
    },
  },
  //using dynamic props with data binding
  /*   methods: {
    setWho(newWho) {
      this.appWho = newWho;
    },
  }, */
};
</script>

<style lang="scss">
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
