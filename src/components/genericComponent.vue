<template>
  <div>
    <h1>{{ title }}</h1>
    <h3>{{ subtitle }}</h3>
    <component :is="currComponent" :options="options" :name="name"/>
  </div>
</template>

<script>
import List from "@/components/forms/formList";
import Textbox from "@/components/forms/formTextbox";
import Checkbox from "@/components/forms/formCheckbox";
export default {
  name: "GenericComponent",
  data() {
    return {
      components: [
        { comp: List, type: "list" },
        { comp: Textbox, type: "textbox" },
        { comp: Checkbox, type: "checkbox" },
      ],
    };
  },
  props: {
    name: { type: String, required: true },
    title: { type: String, required: true },
    subtitle: { type: String, required: false },
    type: { type: String, required: true },
    options: { type: Array, required: false, default: () => [] },
  },
  computed: {
    currComponent() {
      return this.components.find(c => c.type === this.type)?.comp || null; // could be changed to Map but vue has caveat
    },
  },
};
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
h3 {
  margin: 40px 0 0;
}
ul {
  list-style-type: none;
  padding: 0;
}
li {
  display: inline-block;
  margin: 0 10px;
}
a {
  color: #42b983;
}
</style>
