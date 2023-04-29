<template>
  <div class="FormView">
    <fieldset>
      <h2 class="fs-title">Resume/New Application</h2>
      <label>
        <span>Please Enter Email Address</span>
        <input
          :disabled="validated == 1"
          type="text"
          v-model="email"
          name="email"
          placeholder="Email"
        />
      </label>
      <label class="otp-values" v-if="validated == 1">
        <input
          v-validate="'length:1'"
          @input="updateValue"
          ref="OTP1"
          maxlength="1"
          type="number"
          v-model="OTP1"
          name="OTP1"
        />
        <input
          @input="updateValue"
          ref="OTP2"
          maxlength="1"
          type="number"
          v-model="OTP2"
          name="OTP2"
        />
        <input
          @input="updateValue"
          ref="OTP3"
          maxlength="1"
          type="number"
          v-model="OTP3"
          name="OTP3"
        />
        <input
          @input="updateValue"
          ref="OTP4"
          maxlength="1"
          type="number"
          v-model="OTP4"
          name="OTP4"
        />
        <input
          @input="updateValue"
          ref="OTP5"
          maxlength="1"
          type="number"
          v-model="OTP5"
          name="OTP5"
        />
        <input
          @input="updateValue"
          ref="OTP6"
          maxlength="1"
          type="number"
          v-model="OTP6"
          name="OTP6"
        />
      </label>
      <label
        v-if="OTPverified == 1"
        class="msg"
        :class="OTPverified == 0 ? 'error' : 'success'"
        v-text="message"
      ></label>
      <input
        v-if="validated == 0"
        type="submit"
        name="next"
        class="next action-button"
        value="Next"
        v-on:click="sendOTP()"
      />
      <input
        v-else
        type="submit"
        name="submit"
        class="submit action-button"
        value="Submit"
        v-on:click="verifyOTP()"
      />
    </fieldset>
  </div>
</template>

<script>
export default {
  data() {
    return {
      email: "",
      validated: "0",
      message: "",
      OTP1: "",
      OTP2: "",
      OTP3: "",
      OTP4: "",
      OTP5: "",
      OTP6: "",
      OTPverified: "0",
    };
  },
  name: "OTP",
  props: {
    msg: String,
  },
  methods: {
    updateValue(event) {
      const value = event.target.value;
      console.log(value, this.amount);
      console.log(event.target.name);
      if (event.target.name == "OTP1") {
        this.$refs.OTP2.focus();
      }
      if (event.target.name == "OTP2") {
        this.$refs.OTP3.focus();
      }
      if (event.target.name == "OTP3") {
        this.$refs.OTP4.focus();
      }
      if (event.target.name == "OTP4") {
        this.$refs.OTP5.focus();
      }
      if (event.target.name == "OTP5") {
        this.$refs.OTP6.focus();
      }
      if (String(value).length <= 1) {
        this.amount = value;
      }
      value = String(value).substr(-1);
      this.$forceUpdate();
    },
    sendOTP: function () {
      console.log("sendOTP");
      console.log(this.email);
      this.validated = 1;
      console.log(this.validated);
    },
    verifyOTP: function () {
      console.log("sendOTP");
      if (
        this.OTP1 == "1" &&
        this.OTP2 == "2" &&
        this.OTP3 == "3" &&
        this.OTP4 == "4" &&
        this.OTP5 == "5" &&
        this.OTP6 == "6"
      ) {
        this.message = "OTP Verified";
        console.log(this.message);
        this.OTPverified = "1";
        this.$emit("otp-method-step-update", "0");
      } else {
        this.OTPverified = "1";
        this.message = "Try again! OTP not verified";
        console.log(this.message);
      }
    },
  },
};
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
.otp-values {
  display: flex;
}
.otp-values input {
  width: 50px;
  margin: 0 3px;
}
input::-webkit-outer-spin-button,
input::-webkit-inner-spin-button {
  /* display: none; <- Crashes Chrome on hover */
  -webkit-appearance: none;
  margin: 0; /* <-- Apparently some margin are still there even though it's hidden */
}

input[type="number"] {
  -moz-appearance: textfield; /* Firefox */
}
</style>
