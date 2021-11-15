<template> <!-- vue template-->
  <div class="wyr"><!--vue div  class wyr -->
    <!--h2 content-->
    <h2>Please make your choice!</h2>

    <h3>{{ question }}</h3> <!-- I noticed if I had a space between the { { tag is not coding correctly. questionis blue or white. -->
    <!-- inline elements radio button and label.  -->
    <input type="radio" v-model="choice" v-bind:value="answer1" v-on:change="choiceMade">
    <label>{{ answer1 }}</label>
    <!-- radio buttons need values v-binds connects value from our answer without us typing it in again, we can reuse it.  -->
    <input type="radio" v-model="choice" v-bind:value="answer2" v-on:change="choiceMade">
    <label>{{ answer2 }}</label>

  </div> <!-- vue template-->
</template> <!-- vue template-->

<script> //start js script
export default {
  name: 'WouldYouRather', // name edited here . prop is used to send data from the parent
  props: {
    question: String,
    answer1: String,
    answer2: String,   
  },
  data() { //function, returns object
    return{ 
      choice: ''  // we want this to be unique if we have 
    }
  },
  methods:{//method needs help to get a message to the parent. Use "$emit" a vue method event/message 
    choiceMade() {
      this.$emit('answer-changed', this.choice)//can use anyname you like , message sent to-parent. use dash in name to avoid language mixups.
    }
  }
}
//END javascript 
</script>


<!-- Add "scoped" attribute to limit CSS to this component only -->
// <style scoped>
/* starting css Style, scoped limits global useage. per above this component only */
h3 {
  margin: 40px 0 0;
}

.wyr{
  border: 5px black dashed;
  background-color: chartreuse;
}


/* END css style */
</style>
