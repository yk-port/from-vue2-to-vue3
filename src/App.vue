<template>
  <div>
    <BaseInput
      v-model="email"
      @blur="email = 'blurrr@its.cold'"
      label="Email:"
      type="email"
    />
    <pre>{{ email }}</pre>

    <!-- 修飾子やfiltersを使った処理をしたい時は、v-modelの引数に.をつけて -->
    <SalutationName
      v-model:salutation.capitalize="form.salutation"
      v-model:name.capitalize="form.name"
    />
    <pre>{{ form }}</pre>
  </div>
</template>

<script>
// // CompositionAPIの機能,ネストするdataプロパティを作る時にreactiveを使う
// // CompositionAPIの機能,dataプロパティにアクセスする時にrefを使う
import { reactive, ref } from "vue";
import BaseInput from "./components/BaseInput.vue";
import SalutationName from "./components/SalutationName.vue";

export default {
  name: "App",

  components: {
    SalutationName,
    BaseInput,
  },

  setup() {
    // dataプロパティに該当する箇所,formの中にsalutationとnameプロパティがある
    const form = reactive({
      salutation: "",
      name: "",
    });

    const email = ref("");

    return {
      form,
      email,
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
