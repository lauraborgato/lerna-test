<template>
  <div id="app">
    <div>
      <label for="number1">First Number</label>
      <input type="number" id="number1" v-model="number1" />
    </div>
    <div>
      <label for="number2">Second Number</label>
      <input type="number" id="number2" v-model="number2" />
    </div>
    <div>
      <span>{{ add }}</span>
    </div>
    <div>
      <span>{{ substract }}</span>
    </div>
  </div>
</template>

<script lang="ts">
import { Component, Vue } from "vue-property-decorator";
import HelloWorld from "./components/HelloWorld.vue";
import { sum, deduct } from "testlibrary";

@Component({
  components: {
    HelloWorld,
  },
  data() {
    return {
      number1: 0,
      number2: 0,
    };
  },
})
export default class App extends Vue {
  get add() {
    console.log(typeof this.$data.number1);
    return sum(+this.$data.number1, +this.$data.number2);
  }
  get substract(): number {
    return deduct(this.$data.number1, this.$data.number2);
  }
}
</script>

<style lang="scss">
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
