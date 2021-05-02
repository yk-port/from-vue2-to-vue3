<template>
  <div>
    <select @change="updateSalutation">
      <option value="">-</option>
      <option
        v-for="item of salutations"
        :value="item"
        :key="item"
        :selected="salutation === item"
      >
        {{ item }}
      </option>
    </select>

    <input :value="name" type="text" @input="updateName" />
  </div>
</template>

<script>
const salutations = ["Mr", "Mrs", "Miss", "Mx", "Dr"];

export default {
  props: {
    salutation: {
      type: String,
      default: "",
    },
    // 修飾子を受け取るpropsを[props名Modifiers]で定義しておく
    salutationModifiers: {
      default: () => ({}),
    },
    name: {
      type: String,
      default: "",
    },
    // 修飾子を受け取るpropsを[props名Modifiers]で定義しておく
    nameModifiers: {
      default: () => ({}),
    },
  },

  // setup内でpropsの値やemitを使いたい時は、setupの引数に値をセットする
  setup(props, { emit }) {
    const updateSalutation = (event) => {
      let val = event.target.value;
      // propsの中のModifiersに値が存在すれば発火して処理を施すように記述
      if (props.salutationModifiers.capitalize) {
        val = val.toUpperCase();
      }
      emit("update:salutation", val);
    };

    const updateName = (event) => {
      let val = event.target.value;
      if (props.nameModifiers.capitalize) {
        val = val.charAt(0).toUpperCase() + val.slice(1);
      }
      emit("update:name", val);
    };
    return {
      salutations,
      updateSalutation,
      updateName,
    };
  },
};
</script>