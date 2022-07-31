<template>
  <div id="app" style="max-height:9000px">
 
  Welcome to the ARS Travel App!

  
      <amplify-chatbot :chatbotConfig="chatbotConfig"></amplify-chatbot>
  </div>
  


</template>

<script>
import { Interactions } from "aws-amplify";
export default {
  name: "App",
  data: () => ({
    chatbotConfig: {
      bot: "BookTrip_devone",
      clearComplete: false,
    },
  }),
  mounted() {
    Interactions.onComplete("BookTrip_devone", this.handleComplete);
  },
  methods: {
    handleComplete(err, confirmation) {
      if (err) {
        alert("bot conversation failed");
        return;
      }
      alert("done: " + JSON.stringify(confirmation, null, 2));

      return "Trip booked. Thank you! What would you like to do next?";
    },
  },
};

</script>


<style>
main {
  background-color: lightgray;
  background-attachment: fixed;
  
  

}
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: rgb(15, 9, 9);
  margin-top: 70px;
}
</style>