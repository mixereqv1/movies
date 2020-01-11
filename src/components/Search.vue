<template>
  <input name="search" :value="value" @input="handleChange" />
</template>

<script>

export default {
  name: 'Search',
  props: {
    value: {
      type: String,
      required: true,
    },
  },
  methods: {
    handleChange(e) {
      this.$emit('input', e.target.value);
    },
  },
};
</script>

<style lang="scss" scoped>
    input {
      margin-top: 25px;
      color: #fff;
      text-align: center;
      font-size: 18px;
      font-weight: 300;
      height: 30px;
      border: 0;
      background: none;
      border-bottom: 1px solid #fff;
      transition: box-shadow .4s ease-out;

      &:focus {
        outline: none;
        box-shadow: 0 10px 20px -6px rgba(#fff, .4);
      }

      @media (min-width: 768px) {
        font-weight: 400;
      }
    }
</style>
