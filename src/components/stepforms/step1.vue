<template>
  <div class="step">
    <fieldset>
      <h2 class="fs-title">Personal Details</h2>

      <input v-model="name" type="text" name="name" placeholder="Name" />
      <input
        v-model="company"
        type="text"
        name="Company"
        placeholder="Company"
      />
      <input type="text" name="email" placeholder="Email" />
      <input type="text" name="phone" placeholder="Phone" />
    </fieldset>
  </div>
</template>

<script>
export default {
  data() {
    return {
      name: "Xyz",
      company: "isappoasop",
    };
  },
  name: "step1",
  props: {
    msg: String,
  },
};
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
</style>
