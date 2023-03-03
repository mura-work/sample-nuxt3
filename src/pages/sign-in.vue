<script setup>
import ServiceLogo from "../assets/images/main_service_logo.png";
const postFormInput = reactive({
  form: true,
  email: "",
  password: "",
  loging: false,
});

const onSubmitLoginForm = () => {
  console.log({postFormInput});
};

const postFormRules = reactive({
	email: (v) => !!v.match(/^[a-zA-Z0-9._%+-]+@[a-zA-Z0-9.-]+\.[a-zA-Z]{2,}$/),
	password: (v) => !!v.match(/^.{4,12}$/),
})

const openSignUpPage = () => console.log('openSignUpPage')
</script>

<template>
  <div class="sign-in-page">
    <div class="service-content">
      <div>
        <img
          class="inline-block"
          width="85px"
          height="60px"
          :src="ServiceLogo"
          alt=""
        />
      </div>
      <div class="mt-2">
        <span class="font-bold w-16 h-4 text-center">CODECAHT</span>
      </div>
    </div>
    <v-form
      class="w-96 mt-20 mx-auto"
      v-model="postFormInput.form"
      @submit.prevent="onSubmitLoginForm"
    >
      <v-text-field
        v-model="postFormInput.email"
        :readonly="postFormInput.loading"
        :rules="[postFormRules.email]"
        class="mb-2"
        clearable
        label="Email"
      ></v-text-field>

      <v-text-field
        v-model="postFormInput.password"
        :readonly="postFormInput.loading"
        :rules="[postFormRules.password]"
        clearable
        label="Password"
        placeholder="Enter your password"
      ></v-text-field>

      <div>
        <v-chip @click="openSignUpPage" class="font-bold" variant="text">新規登録はこちら</v-chip>
      </div>

      <v-btn
        width="150px"
        :disabled="!postFormInput.form"
        :loading="postFormInput.loading"
        size="large"
        type="submit"
        class="sign-in-button"
      >
        ログイン
      </v-btn>
    </v-form>
  </div>
</template>

<style lang="scss" scoped>
@import "../assets/css/variable.scss";
.sign-in-page {
  background: $primary-background-color;
  height: 100vh;
  padding: 86px 0;

  .service-content {
    margin: 0 auto;
    text-align: center;
  }

  .sign-in-button {
    color: white;
    background-color: #336d95;
  }
}
</style>
