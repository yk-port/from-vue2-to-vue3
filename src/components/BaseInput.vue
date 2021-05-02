<template>
  <label>{{ label }}</label>
  <!-- 親コンポーネントから渡ってくる内容は全てv-bind="$attrs"に内包される -->
  <input
    v-bind="$attrs"
    :value="modelValue"
    @input="$emit('update:modelValue', $event.target.value)"
  />
</template>

<script>
export default {
  // $attrsを使うときの決り文句的な感じで覚えとく
  inheritAttrs: false,
  props: {
    modelValue: {
      type: [String, Number],
      default: "",
    },
    label: {
      type: String,
      default: null,
    },
  },
};
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped></style>
