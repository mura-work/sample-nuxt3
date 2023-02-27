<script setup>
import ServiceLogo from "../assets/images/main_service_logo.png";
import DummyPerson1 from "../assets/images/dummy_person1.png";
</script>

<template>
  <div>
    <div class="header">
      <div>
        <v-img width="35px" height="24px" :src="DummyPerson1" alt=""></v-img>
      </div>
      <div>
        <v-img width="30px" height="30px" :src="ServiceLogo" alt=""></v-img>
      </div>
      <v-btn icon="mdi-magnify" variant="text" color="white"></v-btn>
    </div>
    <slot />
  </div>
</template>

<style scoped lang="scss">
@import "../assets/css/variable.scss";

.header {
  width: 100%;
  height: 40px;
  display: flex;
  justify-content: space-between;
  align-items: center;
  background-color: $main-backgrond-color;
  border-bottom: 2px solid white;
}
</style>
