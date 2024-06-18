<template>
    <div class="container">
      <div class="row justify-content-center">
        <div class="col-12 col-md-6">
          <div class="card mt-5">
            <div class="card-body">
              <input type="text" class="form-control mb-3" v-model="display" disabled />
              <div class="row">
                <button id="numbers" class="btn btn-light col-3" v-for="n in numbers" :key="n" @click="appendNumber(n)">{{ n }}</button>
              </div>
              <div id="signos" class="row mt-3">
                <button class="btn btn-info col-3" @click="setOperation('+')">+</button>
                <button class="btn btn-info col-3" @click="setOperation('-')">-</button>
                <button class="btn btn-info col-3" @click="setOperation('*')">&times;</button>
                <button class="btn btn-info col-3" @click="setOperation('/')">&divide;</button>
              </div>
              <div class="row mt-3">
                <button id="decimal" class="btn btn-secondary col-3" @click="appendNumber('.')">.</button>
                <button id="CE" class="btn btn-danger col-3" @click="clearDisplay">CE</button>
                <button id="igual" class="btn btn-success col-6" @click="calculate">=</button>
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
        display: '',
        currentOperation: null,
        firstOperand: null
      }
    },
    computed: {
      numbers() {
        return [1, 2, 3, 4, 5, 6, 7, 8, 9, 0];
      }
    },
    methods: {
      appendNumber(number) {
        if (number === '.' && this.display.includes('.')) return;
        this.display += number;
      },
      setOperation(operation) {
        if (this.display === '') return;
        this.currentOperation = operation;
        this.firstOperand = parseFloat(this.display);
        this.display = '';
      },
      clearDisplay() {
        this.display = '';
        this.currentOperation = null;
        this.firstOperand = null;
      },
      calculate() {
        if (this.currentOperation === null || this.display === '') return;
        const secondOperand = parseFloat(this.display);
        let result;
        switch (this.currentOperation) {
          case '+':
            result = this.firstOperand + secondOperand;
            break;
          case '-':
            result = this.firstOperand - secondOperand;
            break;
          case '*':
            result = this.firstOperand * secondOperand;
            break;
          case '/':
            result = this.firstOperand / secondOperand;
            break;
          default:
            return;
        }
        this.display = result.toString();
        this.currentOperation = null;
        this.firstOperand = null;
      }
    }
  }
  </script>
  
  <style scoped>
  .card-body{
    background-color: rgb(160, 158, 158);
    border-radius: 20px;
    
  }
  button {
    margin: 5px;
    font-size: 30px
  }
  #numbers{
    background-color:white;
  }
  .btn-info{
    background-color: #50aac7;
    color: white;
   
  }
  
  </style>
  