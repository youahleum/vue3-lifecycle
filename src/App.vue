<template>
  <!-- <h1 v-once @click="add">
    {{ msg }}
  </h1>
  <h1 v-html="msg"></h1> -->
  <Fruits />
  <h1 :[attr]="'active'" @[event]="add">
    {{ msg }}
  </h1>
</template>

<script>
import Fruits from "~/components/Fruits";
// import Fruits from "./components/Fruits.vue";
export default {
  components: { Fruits },
  data() {
    {
      Fruits;
    }
    return {
      // msg: "<div style='color:red;'>hello!!</div>",
      msg: "active",
      attr: "class",
      event: "click",
    };
  },
  methods: {
    add() {
      this.msg += "!";
    },
  },
};
</script>
<style scoped>
.active {
  color: red;
  font-size: 100px;
}
</style>
