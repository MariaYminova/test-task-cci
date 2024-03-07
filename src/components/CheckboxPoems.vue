<template>
  <div class="checkbox-poems">
    <input
      class="checkbox-poems__input"
      type="checkbox"
      :id="id"
      v-model="checkState"
      :disabled="disabled"
    />
    <label class="checkbox-poems__label" :for="id"></label>
  </div>
</template>

<script>
export default {
  name: "CheckboxPoems",

  props: {
    id: {
      type: Number,
      requred: true,
    },

    value: {
      type: Boolean,
      requred: true,
    },

    disabled: {
      type: Boolean,
      default: false,
    },
  },

  emits: ["update:value"],

  computed: {
    checkState: {
      get() {
        return this.value;
      },
      set(value) {
        this.$emit("update:value", value);
      },
    },
  },
};
</script>

<style lang="scss">
.checkbox-poems {

  &__label {
    display: block;
    cursor: pointer;
    width: 30px;
    height: 30px;
    background-color: #000;
    background-color: transparent;
    border: 2px solid #000;

    @media (max-width: 1024px) {
      width: 20px;
      height: 20px;
    }
  }

  &__input {
    display: none;

    &:checked + .checkbox-poems__label {
      background-color: #000;
    }
  }
}
</style>
