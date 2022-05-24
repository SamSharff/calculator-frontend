<template>
  <div class="calculator">
    <!-- <h1>{{ msg }}</h1> -->
    <div class="basic-calculator">
      <div class="display">{{ number || 0 }}</div>
      <div @click="clear" class="btn clear">C</div>
      <div class="btn remove">Del</div>
      <div @click="append(7)" class="btn">7</div>
      <div @click="append(8)" class="btn">8</div>
      <div @click="append(9)" class="btn">9</div>

      <div class="btn operator">/</div>
      <div @click="append(4)" class="btn">4</div>
      <div @click="append(5)" class="btn">5</div>
      <div @click="append(6)" class="btn">6</div>
      <div class="btn operator">x</div>
      <div @click="append(1)" class="btn">1</div>
      <div @click="append(2)" class="btn">2</div>
      <div @click="append(3)" class="btn">3</div>
      <div class="btn operator">-</div>
      <div @click="append(0)" class="btn">0</div>
      <div class="btn">.</div>
      <div class="btn equal">=</div>
      <div class="btn operator">+</div>
    </div>
  </div>
</template>

<script>
export default {
  data: function () {
    return {
      number: 12,
    };
  },
  methods: {
    clear() {
      this.number = "";
    },
    append(num) {
      this.number = `${this.number}${num}`;
    },
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
  grid-column: 3/5;
}
.btn {
  background-color: #f2f2f2;
  border: 1px solid rgb(52, 47, 47);
  cursor: pointer;
}
.equal {
  background-color: red;
  color: white;
}
.operator {
  background-color: rgb(49, 120, 148);
  color: #fff;
}
</style>
