<template> <!-- Vue template parent component, used to show elements we add inside and updates to the browser development server updates browser -->
  <div id="app"> <!--had to add this it was not on my version + the div. Parent, child is  -->

    <h1>Would you rather??</h1>
    <!-- reference to h2 component from would-you-rather template. lower case tag names with dashes identifies its a vue component.  -->
    <would-you-rather 
    v-bind:question="wyrQuestion"
    v-bind:answer1="wyrAnswer1"
    v-bind:answer2="wyrAnswer2"
    v-on:answer-changed="answerChanged"></would-you-rather> 
     <!--data from wouldyourather gets bond to app. Prop data in child=answer1, Parent data wyrAnswer1   -->
    <!-- message to be dispalayed on page is the selection from the binding. -->
    <p> {{ userSelectionMessage }}</p>

  </div><!-- END app DIV.-->
</template>

<script>
//start js script
import WouldYouRather from './components/WouldYouRather.vue'

export default {
  name: 'App',
  components: {
    WouldYouRather
  },
  data(){  // function.
    return{
      wyrQuestion: 'Would you rather never eat cheese again or never drink anything sweet again?',
      wyrAnswer1: 'eat cheese',
      wyrAnswer2: 'Drink anything Sweet',
      userSelectionMessage: ''  //empty string, nothing selected. would you rather app will send data to parent from child.
    }
  },
  methods: {
    answerChanged(choice) {
      this.userSelectionMessage = `Thanks! you chose ${choice}`
    }
  } 
}
//END js script
</script>

<style>
/* Start css style this side is not limited globally? No scope assigned. */
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
  background-color: cornflowerblue;
}

body{
  background-color: darkgrey;
}
/* ending css Style app.vue */
</style>
