<template>
  <section class="FormView" id="FormView">
    <form @submit.prevent="formOnSubmit">
      <step1 v-if="currentStepProp == 1" />

      <fieldset class="form-btn">
        <input
          v-if="currentStepProp > 0"
          type="submit"
          name="previous"
          class="previous action-button"
          value="Previous"
          v-on:click="prevClick()"
        />
        <input
          v-if="currentStepProp < 3 && currentStepProp >= 0"
          type="submit"
          name="next"
          class="next action-button"
          value="Next"
          v-on:click="nextClick()"
        />
        <input
          v-else
          type="submit"
          name="submit"
          class="submit action-button"
          value="Submit"
        />
        {{ currentStepProp }}
      </fieldset>
      <h6>{{ formFields.name }}</h6>
    </form>
  </section>
</template>



<script>
import step1 from "./stepforms/step1";

export default {
  data() {
    return {
      // Initialize the form field (STEP 1)
      formFields: {
        name: "xzas",
        email: "",
        password: "",
        moreData: {
          field1: "",
          field2: [],
        },
      },
      // Create an object property used for cloning (STEP 2)
      formFieldsCopy: {},
    };
  },

  name: "FormView",
  props: ["currentStepProp"],
  // props: {
  //   currentStepProp: Number,
  // },
  components: {
    step1,
  },
  methods: {
    nextClick: function () {
      console.log("clicked");
      //this.formFields.name = "errrrrrr";
      ++this.currentStepProp;
      //this.$emit("currentStepProp", currentStepProp);
    },
    prevClick: function () {
      console.log("clicked");
      //this.formFields.name = "errrrrrr";
      --this.currentStepProp;
    },
    formOnSubmit: function (submitEvent) {
      //alert("sumitted");
      console.log("Name:" + this.name);
      this.$emit("child-method", this.currentStepProp);
    },
  },
};
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->

