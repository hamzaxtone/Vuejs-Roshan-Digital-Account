<template>
  <div id="app">
    <div class="otp-sec" v-if="currentStep == 'otp'">
      <OTP v-on:otp-method-step-update="otp_method_step_update" />
    </div>
    <div class="form-sec" v-else>
      <HelloWorld msg="Hello Vue in CodeSandbox!" />
      <ProgressBar
        v-if="currentStep"
        :currentStepProp="currentStep"
      ></ProgressBar>
      <FormView
        :currentStepProp="currentStep"
        v-on:child-method="updateParentStep"
      ></FormView>
    </div>
    {{ currentStep }}
  </div>
</template>

<script>
import HelloWorld from "./components/HelloWorld";
import ProgressBar from "./components/ProgressBar";
import FormView from "./components/FormView";
import OTP from "./components/otp/otp";

export default {
  data() {
    return {
      currentStep: "otp",
    };
  },
  name: "App",
  components: {
    HelloWorld,
    ProgressBar,
    FormView,
    OTP,
  },
  methods: {
    updateParentStep(value_from_child) {
      this.currentStep = value_from_child;
      console.log("value_from_child " + value_from_child);
    },
    otp_method_step_update(stepNum) {
      console.log(this.email);
      this.currentStep = stepNum;
    },
  },
};
</script>

<style>
#app {
  font-family: "Avenir", Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
@import url(https://fonts.googleapis.com/css?family=Montserrat);

/*basic reset*/

* {
  margin: 0;
  padding: 0;
}

html {
  height: 100%;
  -webkit-background-size: cover;
  -moz-background-size: cover;
  -o-background-size: cover;
  background-size: cover;
  background:#00a892;
  background-repeat:no-repeat;
 	background-image: -webkit-gradient(linear, left top, left bottom, from(#00353b), to(#00a892));
	background-image: -webkit-linear-gradient(top, #00353b, #00a892);
	background-image: -moz-linear-gradient(top, #00353b, #00a892);
	background-image: -ms-linear-gradient(top, #00353b, #00a892);
	background-image: -o-linear-gradient(top, #00353b, #00a892);
	background-image: linear-gradient(top, #00353b, #00a892);
	filter: progid:DXImageTransform.Microsoft.gradient(start-colourStr='#00353b', end-colourStr='#00a892');
	

}

body {
  font-family: 'Montserrat', arial, verdana;
   
}
</style>
<style >
/*form styles*/

.FormView fieldset {
  background: white;
  border: 0 none;
  border-radius: 3px;
  box-shadow: 0 0 15px 1px rgba(0, 0, 0, 0.4);
  padding: 20px 30px;
  box-sizing: border-box;
  width: 80%;
  margin: 0 auto 15px;
  /*stacking fieldsets above each other*/
  position: relative;
}

/*Hide all except first fieldset*/

.FormView fieldset:not(:first-of-type) {
  display: none;
}

/*inputs*/
.FormView label {
  text-align: left;
  display: block;
}

.FormView label span {
  font-weight: 600;
  padding: 4px 0px;
  display: block;
}

.FormView input,
.FormView textarea,
.FormView select {
  padding: 15px;
  border: 1px solid #ccc;
  border-radius: 3px;
  margin-bottom: 10px;
  width: 100%;
  box-sizing: border-box;
  font-family: "Montserrat";
  color: #2C3E50;
  font-size: 13px;
}

/*buttons*/

.FormView .action-button {
  width: 100px;
  background: #27AE60;
  font-weight: bold;
  color: white;
  border: 0 none;
  border-radius: 1px;
  cursor: pointer;
  padding: 10px 5px;
  margin: 10px 5px;
}

.FormView .action-button:hover,
.FormView .action-button:focus {
  box-shadow: 0 0 0 2px white, 0 0 0 3px #27AE60;
}

/*headings*/

.fs-title {
  font-size: 15px;
  text-transform: uppercase;
  color: #2C3E50;
  margin-bottom: 10px;
}

.fs-subtitle {
  font-weight: normal;
  font-size: 13px;
  color: #666;
  margin-bottom: 20px;
  text-align: left;
}
</style>