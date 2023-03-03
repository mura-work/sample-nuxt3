<script setup>
import ServiceLogo from "../assets/images/main_service_logo.png";
const postFormInput = reactive({
  form: true,
	name: "",
  email: "",
  password: "",
  loging: false,
});

const onSubmitLoginForm = () => {
  console.log({postFormInput});
};

const postFormRules = reactive({
	name: (v) => !!v,
	email: (v) => !!v && !!v.match(/^[a-zA-Z0-9._%+-]+@[a-zA-Z0-9.-]+\.[a-zA-Z]{2,}$/),
	password: (v) => !!v && !!v.match(/^.{4,12}$/),
})

</script>

<template>
  <div class="sign-up-page">
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
        v-model="postFormInput.name"
        :readonly="postFormInput.loading"
        :rules="[postFormRules.name]"
        class="mb-2"
        clearable
        label="Name"
      />
      <v-text-field
        v-model="postFormInput.email"
        :readonly="postFormInput.loading"
        :rules="[postFormRules.email]"
        class="mb-2"
        clearable
        label="Email"
      />

      <v-text-field
        v-model="postFormInput.password"
        :readonly="postFormInput.loading"
        :rules="[postFormRules.password]"
        clearable
        label="Password"
				type="password"
        placeholder="Enter your password"
      />

      <v-btn
        width="150px"
        :disabled="!postFormInput.form"
        :loading="postFormInput.loading"
        size="large"
        type="submit"
        class="sign-up-button"
      >
        新規登録
      </v-btn>
    </v-form>
  </div>
</template>

<style lang="scss" scoped>
@import "../assets/css/variable.scss";
.sign-up-page {
  background: $primary-background-color;
  height: 100vh;
  padding: 86px 0;

  .service-content {
    margin: 0 auto;
    text-align: center;
  }

  .sign-up-button {
    color: white;
    background-color: #336d95;
  }
}
</style>
