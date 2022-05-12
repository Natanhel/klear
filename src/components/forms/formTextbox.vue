<template>
  <div>
    <!-- <h1>{{ textValue }}</h1> -->
    <input type="text" v-model="textValue" :placeholder="options.hint">
  </div>
</template>

<script>
export default {
  props: {
    name: { type: String, required: true },
    options: { type: Object, required: false, default: () => {} },
  },
  data() {
    return {
      textValue: "",
    };
  },
  methods: {
      onTextChange(){
          // TODO save text to state
      }
  }
};
</script>

<style>
</style>