<template>
  <div>
    <SalutationName
      v-model:salutation="form.salutation"
      v-model:name="form.name"
    />
    <pre>{{ form }}</pre>
  </div>
</template>

<script>
// // CompositionAPIの機能,ネストするdataプロパティを作る時に使う
import { reactive } from "vue";
import SalutationName from "./components/SalutationName.vue";

export default {
  name: "App",

  components: {
    SalutationName,
  },

  setup() {
    // dataプロパティに該当する箇所,formの中にsalutationとnameプロパティがある
    const form = reactive({
      salutation: "",
      name: "",
    });

    return {
      form,
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
