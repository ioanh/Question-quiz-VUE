<template>
  <div id="app">
    <Header
      v-if="questions.length"
      :numCorrect="numCorrect"
      :numTotal="numTotal"
     />
    <b-container class="bv-example-row">
    <b-row>
      <b-col sm="6" offset="3">
        <QuestionBox
          v-if="questions.length" 
          :currentQuestion="questions[index]"
          :next="next"
          :increment="increment"
        />
      </b-col>
    </b-row>
  </b-container>
  </div>
</template>

<script>
/*IMPORTS*/
import Header from './components/Header.vue'
import QuestionBox from './components/QuestionBox.vue'
import Vue from 'vue'
import { BootstrapVue, IconsPlugin } from 'bootstrap-vue'
import 'bootstrap/dist/css/bootstrap.css'
import 'bootstrap-vue/dist/bootstrap-vue.css'

// Install BootstrapVue
Vue.use(BootstrapVue)
// Optionally install the BootstrapVue icon components plugin
Vue.use(IconsPlugin)
/*INITIALIZING THE APP COMPONENT*/
export default {
  name: 'App',
  /*IMPORTING COMPONENTS*/
  components: {
    Header,
    QuestionBox
  },
  data() {
    return {
      questions: [],
      index: 0,
      numCorrect: 0,
      numTotal: 0
    }
  },
  methods:{
    /* INCREMENTING THE INDEX OF THE CURRENT QUESTION EVERY TIME WHEN THE NEXT BUTTON IS CLICKED IN THE QUESTIONBOX COMPONENT*/
    next() {
      this.index++
    },/*INCREMENTING THE CORRECTANSWERS, TOTALANSWERED COUNTERS IN THE HEADER COMPONENT*/
    increment(isCorrect) {
      if(isCorrect) {
        this.numCorrect++
      }
      this.numTotal++
    }
  },
  mounted() {
    /*REQUESTING THE API*/
    fetch('https://opentdb.com/api.php?amount=10&category=27&type=multiple', {
      method: 'get'
    })/*RESOLVING THE PROMISE*/
      .then((response) => {
        return response.json()
      })/*FILLING UP THE QUESTIONS ARRAY WITH THE RESULTS FROM THE JSON FILE*/
      .then((jsonData) => {
        this.questions = jsonData.results
      })
  }
}
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
