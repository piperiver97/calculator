<template>
  <div class="container">
    <div class="row justify-content-center">
      <div class="col-12 col-md-6">
        <div class="calculator card mt-5 mb-5">
          <div class="card-body">
            <input type="text" class="calculator-screen z-depth-1 form-control mb-3" v-model="display" disabled />
            <div class="calculator-keys">
              <div class="row mb-2 justify-content-center">
                <button class="operator btn col m-1" @click="setOperation('+')">+</button>
                <button class="operator btn col m-1" @click="setOperation('-')">-</button>
                <button class="operator btn col m-1" @click="setOperation('*')">&times;</button>
                <button class="operator btn col m-1" @click="setOperation('/')">&divide;</button>
              </div>
              <div class="row mb-2 justify-content-center">
                <button class="btn btn-light col m-1" @click="appendNumber(7)">7</button>
                <button class="btn btn-light col m-1" @click="appendNumber(8)">8</button>
                <button class="btn btn-light col m-1" @click="appendNumber(9)">9</button>
              </div>
              <div class="row mb-2 justify-content-center">
                <button class="btn btn-light col m-1" @click="appendNumber(4)">4</button>
                <button class="btn btn-light col m-1" @click="appendNumber(5)">5</button>
                <button class="btn btn-light col m-1" @click="appendNumber(6)">6</button>
              </div>
              <div class="row mb-2 justify-content-center">
                <button class="btn btn-light col m-1" @click="appendNumber(1)">1</button>
                <button class="btn btn-light col m-1" @click="appendNumber(2)">2</button>
                <button class="btn btn-light col m-1" @click="appendNumber(3)">3</button>
              </div>
              <div class="row mb-2 justify-content-center">
                <button class="decimal function btn col m-1" @click="appendNumber('.')">.</button>
                <button class="btn btn-light col m-1" @click="appendNumber(0)">0</button>
                <button class="all-clear function btn col m-1" @click="clearDisplay">AC</button>
              </div>
              <div class="row mb-2 justify-content-center">                
                <button class="equal-sign operator btn col m-1 " @click="calculate">=</button>
              </div>
            </div>
          </div>
        </div>
      </div>
    </div>
  </div>
</template>
<script>
export default {
  data() {
    return {
      display: "",
      currentOperation: null,
      firstOperand: null,
    };
  },
  methods: {
    appendNumber(number) {
      if (number === "." && this.display.includes(".")) return;
      this.display += number;
    },
    setOperation(operation) {
      if (this.display === "") return;
      this.currentOperation = operation;
      this.firstOperand = parseFloat(this.display);
      this.display = "";
    },
    clearDisplay() {
      this.display = "";
      this.currentOperation = null;
      this.firstOperand = null;
    },
    calculate() {
      if (this.currentOperation === null || this.display === "") return;
      const secondOperand = parseFloat(this.display);
      let result;
      switch (this.currentOperation) {
        case "+":
          result = this.firstOperand + secondOperand;
          break;
        case "-":
          result = this.firstOperand - secondOperand;
          break;
        case "*":
          result = this.firstOperand * secondOperand;
          break;
        case "/":
          result = this.firstOperand / secondOperand;
          break;
        default:
          return;
      }
      this.display = result.toString();
      this.currentOperation = null;
      this.firstOperand = null;
    },
  },
};
</script>

<style scoped>

.calculator {
  background-color: rgb(66, 66, 66);
  border-radius: 20px;
}
.calculator-screen {
  width: 100%;
  height: 80px;
  background-color: #ffffff;
  border: none;
  border-radius: 5px;
  margin-bottom: 20px;
  text-align: right;
  padding: 10px;
  font-size: 2em;
}
button {
  height: 60px;
  font-size: 1.5em;
}
.operator {
  background-color: #4bade2;
  color: white;
}

.operator:hover {
  color: #fff;
  background-color: #93ddff;
  border-color: #93ddff;
}

.btn-light {
  background-color: white;
}
.decimal {
  background-color: #4bade2;
  color: white;
}

.decimal:hover {
  color: #fff;
  background-color: #93ddff;
  border-color: #93ddff;
}

.all-clear {
  background-color: #4bade2;
  color: white;
}

.all-clear:hover {
  color: #fff;
  background-color: #93ddff;
  border-color: #93ddff;
}

.equal-sign {
  background-color: #4bade2;
  color: white;
}

</style>
