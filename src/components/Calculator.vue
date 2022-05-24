<template>
  <div class="calculator">
    <h1>{{ msg }}</h1>
    <div class="basic-calculator">
      <div>Hello</div>
      <div>Hello</div>
      <div>Hello</div>
      <div>Hello</div>
      <div>Hello</div>
      <div>Hello</div>
    </div>
  </div>
</template>

<script>
export default {
  name: "HelloWorldCalculator",
  props: {
    msg: String,
  },
};
</script>

Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
.basic-calculator {
  display: grid;
  grid-template-columns: repeat(4, 1fr);
  grid-auto-rows: minmax(50px, auto);
  margin: 0 auto;
  width: 400px;
  font-size: 40px;
}
.display {
  grid-column: 1/5;
  background-color: #444 !important;
  color: #fff;
}
.clear {
  grid-column: 1/3;
}
.remove {
  grid-column: 1/3;
}
.btn {
  background-color: #f2f2f2;
  border: 1px solic #999;
  cursor: pointer;
}
.operator {
  background-color: rgb(49, 120, 148);
  color: #fff;
}
</style>
