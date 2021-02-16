<template>
  <div class="sign-up">
    <!-- <Button
      text="Default btn"
      style="margin-bottom:20px"
      @click.native="submitForm"
    />
    <Button disabled text="Disabled btn" />
    <TextField
      :value="controllValue"
      @input="controllValue = $event"
      :validationMessage="controllValidate"
    />
    <TextField placeholder="It's a placeholder." label="Some label" /> -->
    <DropDown />
    <CheckBox />
  </div>
</template>

<script>
import { required, minLength } from "vuelidate/lib/validators";
// import Button from "../components/Button";
// import TextField from "../components/TextField";
import DropDown from "../components/DropDown";
import CheckBox from "../components/CheckBox";

export default {
  components: {
    // Button,
    // TextField,
    DropDown,
    CheckBox
  },
  data() {
    return {
      controllValue: "123",
      isSended: false
    };
  },
  validations: {
    controllValue: {
      required,
      minLength: minLength(4)
    }
  },
  computed: {
    controllValidate() {
      if (this.isSended) {
        if (!this.$v.controllValue.required) {
          return "It's field required";
        }

        if (!this.$v.controllValue.minLength) {
          return "Field must be have a minimum length of 4";
        }
      }

      return "";
    }
  },
  methods: {
    submitForm() {
      console.log(this.$v.$invalid);
      this.isSended = true;
    }
  }
};
</script>

<style lang="scss">
.sign-up {
  display: flex;
  flex-direction: column;
  padding: 40px 30px;
}
</style>
