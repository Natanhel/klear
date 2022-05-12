<template>
  <div id="app">
    <GenericComponent
      :name="name"
      :title="title"
      :subtitle="subtitle"
      :type="type"
      :options="options"
    />
    <button v-on:click="back">Back</button>
    {{ index + 1 }} / {{ this.components.length }}
    <button v-on:click="next">Next</button>
  </div>
</template>

<script>
import GenericComponent from "./components/genericComponent.vue";

export default {
  name: "App",
  components: {
    GenericComponent,
  },
  data() {
    return {
      index: 0,

      name: "",
      title: "",
      subtitle: "",
      type: null,
      options: [],
    };
  },
  created() {
    // make a backend call to get every possible component
    // this is mock
    this.components = [
      {
        name: "welcome",
        type: "textbox",
        title: "Welcome!",
        subtitle: "How should we call you?",
        options: { hint: "Name" },
      },
      {
        name: "expertise",
        type: "checkbox",
        title: "Hey $nameValue$!",
        subtitle: "What are your expertise?",
        options: {
          whereToGetNameFrom: "welcome", // unique name
          checkboxOptions: ["Lifestyle", "Beauty", "Food"],
        },
      },
      {
        name: "lastThing",
        type: "list",
        title: "One last thing",
        subtitle: "Have you collaborated with brands in the past?",
        options: {
          hint: "Enter Brand Name",
          listOptions: ["Nike", "Coca Cola", "Meltwater", "Klear"],
        },
      },
    ];
    this.updateGenericComponentData();
  },
  methods: {
    updateGenericComponentData() {
      this.name = this.components[this.index].name;
      this.title = this.components[this.index].title;
      this.subtitle = this.components[this.index].subtitle;
      this.type = this.components[this.index].type;
      this.options = this.components[this.index].options;
    },
    next() {
      if (this.index + 1 === this.components.length) {
        return;
      }
      this.index++;
      this.updateGenericComponentData();
    },
    back() {
      if (this.index === 0) {
        return;
      }
      this.index--;
      this.updateGenericComponentData();
    },
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
