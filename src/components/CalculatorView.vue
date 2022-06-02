<template>
  <div class="calculator">
    <!-- <h1>{{ msg }}</h1> -->
    <div class="basic-calculator">
      <div class="display">{{ number || 0 }}</div>
      <div @click="clear" class="btn clear hover-class">C</div>
      <div @click="remove" class="btn remove hover-class">Del</div>
      <div @click="append(7)" class="btn hover-class">7</div>
      <div @click="append(8)" class="btn hover-class">8</div>
      <div @click="append(9)" class="btn hover-class">9</div>

      <div @click="division" class="btn operator hover-class-operator">/</div>
      <div @click="append(4)" class="btn hover-class">4</div>
      <div @click="append(5)" class="btn hover-class">5</div>
      <div @click="append(6)" class="btn hover-class">6</div>
      <div @click="multiplication" class="btn operator hover-class-operator">x</div>
      <div @click="append(1)" class="btn hover-class">1</div>
      <div @click="append(2)" class="btn hover-class">2</div>
      <div @click="append(3)" class="btn hover-class">3</div>
      <div @click="subtraction" class="btn operator hover-class-operator">-</div>
      <div @click="append(0)" class="btn hover-class">0</div>
      <div @click="dot" class="btn hover-class">.</div>
      <div @click="equal" class="btn operator hover-class-operator">=</div>
      <div @click="addition" class="btn operator hover-class-operator">+</div>
    </div>
  </div>
</template>

<script>
export default {
  data: function () {
    return {
      prevNum: null,
      number: "",
      operator: null,
      clickedOperator: false,
    };
  },
  methods: {
    clear() {
      this.number = "";
    },
    append(num) {
      if (this.clickedOperator) {
        (this.number = ""), (this.clickedOperator = false);
      }
      this.number = `${this.number}${num}`;
    },
    dot() {
      if (this.number.indexOf(".") === -1) {
        this.append(".");
      }
    },
    remove() {
      this.number = this.number.slice(0, -1);
    },
    setPrevNum() {
      this.prevNum = this.number;
      this.clickedOperator = true;
    },
    addition() {
      this.operator = (a, b) => a + b;
      this.setPrevNum();
    },
    subtraction() {
      this.operator = (a, b) => a - b;
      this.setPrevNum();
    },
    multiplication() {
      this.operator = (a, b) => a * b;
      this.setPrevNum();
    },
    division() {
      this.operator = (a, b) => a / b;
      this.setPrevNum();
    },
    equal() {
      this.number = `${this.operator(parseFloat(this.prevNum), parseFloat(this.number))}`;
      this.prevNum = "";
      // if (isNaN(number) || isNaN(prevNum)) return;
      // Working on: getting this function not to run if value is NaN
      // Working on: getting calculator to handle multiple arguments in format "number + number + number", etc. instead of hvaing to press "=" in between each computation
    },
  },
};
</script>

Add "scoped" attribute to limit CSS to this component only -->
<style>
body {
  padding: 0;
  margin: 0;
  background: linear-gradient(to right, rgb(255, 255, 241), #a1aba4);
}
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
  color: rgb(255, 255, 241);
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

.hover-class:hover {
  cursor: pointer;
  background: rgb(255, 255, 241);
}

.hover-class-operator:hover {
  cursor: pointer;
  color: #444 !important;
}

.operator {
  background-color: #a1aba4;
  color: rgb(255, 255, 241);
}
</style>
