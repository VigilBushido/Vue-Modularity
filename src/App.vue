<template>
  <div id="app">
    <!--<Greeting greeting="Hi" who="Everyone" /> -->

    <!-- using dynamic props with data binding -->
    <!--     <Hello greeting="Hello" v-bind:who="appWho" />
    <button @click="setWho('JavaScript')">JavaScript</button>
    <button @click="setWho('Everyone')">Everyone</button> -->

    <!--     <Greeting :greeting="greeting" :who="who" />
    <button @click="newGreeting()">New Greeting</button> -->

    <!-- Prop Typing and Validation -->
    <!-- our Repeat component will be consumed as follows -->
    <!-- static <Repeat :config="{ times: 3, content: 'Repeat me.' }" /> -->
    <!--     <RepeatTyped :times="count" content="Repeat." />
    <button @click="increment()">Repeat</button> -->
    <!--<RepeatTyped :times="count" :content="55" />  causes the 2 errors to occur -->

    <!--<CustomSelect :selected="selected" :options="options" /> -->

    <!--     <PaginatedList :items="snacks" :offset="offset" :limit="limit" />

    <button @click="offset++">Increment Offset (current: {{ offset }})</button>
    <button @click="limit++">Increment Limit (current: {{ limit }})</button> -->

    <Repeat :config="{ times: 3, content: 'Repeat me.' }" />
  </div>
</template>

<script>
//import Greeting from "./components/Greeting";
//import Repeat from "./components/Repeat";
//import RepeatTyped from "./components/RepeatTyped";
//import Hello from "./components/Hello"; // using dynamic props with data binding
//import CustomSelect from "./components/CustomSelect";
//import PaginatedList from "./components/PaginatedList.vue";
import Repeat from "./components/Repeat.vue";

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
    //Greeting,
    //Repeat,
    //RepeatTyped,
    //CustomSelect,
    //PaginatedList,
    Repeat,
    //Hello,
  },
  data() {
    return {
      offset: 0,
      limit: 0,
      snacks: [
        {
          id: "ready-salted",
          content: "Ready Salted",
        },
        {
          id: "spicy-jalepeno",
          content: "Spicy & Japleno",
        },
        {
          id: "salt-vinegar",
          content: "Salt & Vinegar",
        },
      ],
      //appWho: "Vue.js", // using dynamic props with data binding
      //4.02 below we make a greeting app
      /*    greeting: "Hello",
      who: "Vue.js",   // we refactor this so it only holds default index*/
      currentIndex: 0,
      //count: 1,
      count: "no-number-here",

      //Custom validation of Array's, Object shapes, and more with Validators
      selected: "salt-vinegar",
      options: [
        {
          value: "ready-salted",
          label: "Ready Salted",
        },
        {
          value: "cheese-onion",
          label: "Cheese & Onion",
        },
        {
          value: "salt-vinegar",
          label: "Salt & Vinegar", // removing a label will cause the prop validator in app to signal
        },
      ],
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
    increment() {
      this.count += 1;
    },
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
