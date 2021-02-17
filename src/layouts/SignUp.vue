<template>
  <div class="sign-up">
    <h2 class="sign-up__title">
      Регистрация
    </h2>
    <div class="sign-up__login">
      <span>Уже есть аккаунт?</span>
      <a href="#">Войти</a>
    </div>
    <div class="sign-up__field">
      <TextField
        :value="name"
        @input="name = $event"
        :validationMessage="controllValidate"
        placeholder="Введите ваше имя"
        label="Имя"
        class="sign-up__field"
      />
      <TextField
        :value="email"
        @input="email = $event"
        :validationMessage="controllValidate"
        placeholder="Введите ваш email"
        label="Email"
        class="sign-up__field"
      />
      <TextField
        :value="phone"
        @input="phone = $event"
        :validationMessage="controllValidate"
        placeholder="Введите номер телефон"
        label="Номер телефона"
        class="sign-up__field"
      />
      <DropDown
        :values="langValues"
        :currentValue="langValue"
        :opened="langDropDownOpened"
        @toggleOpen="langDropDownOpened = !langDropDownOpened"
        @selectValue="langValue = $event"
        label="Язык"
      />
    </div>
    <div class="sign-up__accept">
      <CheckBox v-model="acceptChecked" :checked="acceptChecked" />
      <div class="sign-up__accept__text">
        Принимаю <a href="#">условия</a> использования
      </div>
    </div>
    <Button
      text="Зарегистрироваться"
      style="margin-bottom:20px"
      @click.native="submitForm"
      :disabled="submitDisabled"
    />
  </div>
</template>

<script>
import { required, email } from "vuelidate/lib/validators";
import TextField from "../components/TextField";
import DropDown from "../components/DropDown";
import CheckBox from "../components/CheckBox";
import Button from "../components/Button";

const validateName = value => value.match(/[^а-яёa-z -]/i) === null;
const validatePhoneNumber = number =>
  !!number.match(/^(\s*)?(\+)?([- _():=+]?\d[- _():=+]?){10,14}(\s*)?$/i);

export default {
  components: {
    TextField,
    DropDown,
    CheckBox,
    Button
  },
  data() {
    return {
      name: "",
      email: "",
      phone: "",
      langValue: "Русский",
      langValues: ["Русский", "Английский", "Китайский", "Испанский"],
      langDropDownOpened: false,
      acceptChecked: false
    };
  },
  validations: {
    name: {
      required,
      validateName
    },
    email: {
      required,
      email
    },
    phone: {
      required,
      validatePhoneNumber
    },
    acceptChecked: {
      isChecked: checked => checked
    }
  },
  computed: {
    controllValidate() {
      if (this.isSended) {
        // if (!this.$v.controllValue.required) {
        //   return "It's field required";
        // }
        // if (!this.$v.controllValue.minLength) {
        //   return "Field must be have a minimum length of 4";
        // }
      }

      return "";
    },
    submitDisabled() {
      return this.$v.$invalid ? true : false;
    }
  },
  methods: {
    submitForm() {
      this.isSended = true;
    }
  }
};
</script>

<style lang="scss">
.sign-up {
  width: calc(99vw - 60px);
  height: calc(99vh - 80px);
  display: flex;
  flex-direction: column;
  justify-content: space-between;
  padding: 40px 30px;
  overflow-y: auto;

  background: #ffffff;
  box-shadow: 0px 12px 24px rgba(44, 39, 56, 0.02),
    0px 32px 64px rgba(44, 39, 56, 0.04);
  border-radius: 24px;

  &__title {
    font-weight: bold;
    font-size: 34px;
    line-height: 44px;
    color: #2c2738;

    margin-bottom: 6px;
  }

  &__login {
    font-size: 16px;
    line-height: 22px;
    margin-bottom: 56px;

    & > a {
      margin-left: 6px;
      color: #0880ae;
      text-decoration: none;
    }
  }

  &__field {
    margin-bottom: 34px;
  }

  &__accept {
    display: flex;
    align-items: center;
    margin: 30px 0;

    &__text {
      margin-left: 5px;
      font-size: 16px;
      line-height: 22px;
      font-weight: 500;
      color: #756f86;

      & > a {
        color: #0880ae;
        font-weight: 500;
        text-decoration: none;
      }
    }
  }
}

@media (min-width: 480px) and (max-width: 760px) {
  .sign-up {
    width: calc(95vw - 60px);
    height: calc(95vh - 80px);
  }
}

@media (min-width: 760px) and (max-width: 1440px) {
  .sign-up {
    width: calc(90vw - 60px);
  }
}

@media (min-width: 1440px) {
  .sign-up {
    width: calc(80vw - 60px);
  }
}
</style>
