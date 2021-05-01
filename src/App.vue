<template>
  <div>
    <BaseInput v-model:modelValue="myInput" />
    <pre>{{ $data }}</pre>
  </div>
</template>

<script>
import BaseInput from "./components/BaseInput.vue";
export default {
  name: "App",
  components: {
    BaseInput,
  },
  data() {
    return {
      myInput: "",
    };
  },
};
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
