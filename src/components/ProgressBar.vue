<template>
  <section class="progressBar-sec">
    <ul id="progressbar">
      <!-- <li class="active" id="account"><strong>Account</strong></li>
      <li id="personal"><strong>Personal</strong></li>
      <li id="payment"><strong>Image</strong></li>
      <li id="confirm"><strong>Finish</strong></li> -->
      <li
        v-for="(value, index) in steps"
        :key="index"
        :id="value.id"
        :class="index == currentStepProp ? 'active' : 'not-active'"
      >
        <strong>{{ value.name }}</strong>
      </li>
    </ul>
    {{ currentStepProp }}

    <div></div>
  </section>
</template>

<script>
export default {
  data() {
    return {
      steps: [
        { name: "Account", id: "account" },
        { name: "Personal", id: "personal" },
        { name: "Image", id: "image" },
        { name: "Finish", id: "finish" },
      ],
    };
  },
  props: ["currentStepProp"],
  name: "ProgressBar",
  // props: {
  //   msg: String,
  // },
};
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style>
/*form styles*/

.progressBar-sec {
  width: 100%;
  max-width: 1170px;
  margin: 50px auto;
  text-align: center;
  position: relative;
  padding: 0 15px;
}

/*progressbar*/

#progressbar {
  margin-bottom: 30px;
  overflow: hidden;
  /*CSS counters to number the steps*/
  counter-reset: step;
  display: flex;
}

#progressbar ul {
  padding-left: 0px !important;
}

#progressbar li {
  list-style-type: none;
  color: #000;
  text-transform: uppercase;
  font-size: 9px;
  width: 50%;
  float: left;
  position: relative;
}

#progressbar li:before {
  content: counter(step);
  counter-increment: step;
  width: 20px;
  line-height: 20px;
  display: block;
  font-size: 10px;
  color: #333;
  background: green;
  border-radius: 3px;
  margin: 0 auto 5px auto;
}

/*progressbar connectors*/

#progressbar li:after {
  content: "";
  width: 100%;
  height: 2px;
  background: green;
  position: absolute;
  left: -50%;
  top: 9px;
  z-index: -1;
  /*put it behind the numbers*/
}

#progressbar li:first-child:after {
  /*connector not needed before the first step*/
  content: none;
}

/*marking active/completed steps green*/

/*The number of the step and the connector before it = green*/

#progressbar li.active:before,
#progressbar li.active:after {
  background: #eee809;
  color: #00353b;
}
</style>
