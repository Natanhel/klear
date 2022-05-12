<template>
  <div>
      <ul>
          <li v-for="checkName in options.checkboxOptions" :key="checkName">
            <input type="checkbox" :id="checkName" :value="checkName" v-model="check">
            <label :for="checkName">{{checkName}}</label>   
          </li>
      </ul>
  </div>
</template>

<script>
export default {
  props: {
    name: { type: String, required: true },
    options: { type: Object, required: false, default: () => {} },
  },
}
</script>

<style>

</style>