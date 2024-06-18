<template>
    <div class="currency-converter card">
      <h2>Currency Converter</h2>
      <div class="form-group">
        <label for="amount">Amount</label>
        <input type="number" v-model.number="amount" class="form-control" id="amount" />
      </div>
      <div class="form-group">
        <label for="fromCurrency">From</label>
        <select v-model="fromCurrency" class="form-control" id="fromCurrency">
          <option v-for="currency in currencies" :key="currency" :value="currency">{{ currency }}</option>
        </select>
      </div>
      <div class="form-group">
        <label for="toCurrency">To</label>
        <select v-model="toCurrency" class="form-control" id="toCurrency">
          <option v-for="currency in currencies" :key="currency" :value="currency">{{ currency }}</option>
        </select>
      </div>
      <button @click="convert" id="convert-btn" class="btn">Convert</button>
      <h3 v-if="result">{{ amount }} {{ fromCurrency }} = {{ result }} {{ toCurrency }}</h3>
    </div>
  </template>
  
  <script>
  export default {
    data() {
      return {
        amount: 0,
        fromCurrency: 'EUR',
        toCurrency: 'USD',
        result: null,
        currencies: ['EUR', 'USD', 'JPY', 'HNL'],
        rates: {
          EUR: { USD: 1.1, JPY: 130, HNL: 27 },
          USD: { EUR: 0.91, JPY: 118, HNL: 24.5 },
          JPY: { EUR: 0.0077, USD: 0.0085, HNL: 0.21 },
          HNL: { EUR: 0.037, USD: 0.041, JPY: 4.8 }
        }
      };
    },
    methods: {
      convert() {
        if (this.fromCurrency === this.toCurrency) {
          this.result = this.amount;
        } else {
          const rate = this.rates[this.fromCurrency][this.toCurrency];
          this.result = (this.amount * rate).toFixed(2);
        }
      }
    }
  };
  </script>
  
  <style scoped>
  .currency-converter {
    width: 100%;
    max-width: 400px;
    margin: auto;
    padding: 20px;
    border-radius: 10px;
    box-shadow: 0 0 20px rgba(0, 0, 0, 0.1);
    margin-top:80px;
    background-color: rgb(66, 66, 66);
    color: white;
  }

  .form-group{
    margin-top: 10px;
  }


  #convert-btn{
    background-color: #4bade2;
    color: white;
    margin-top:30px;
  }  

  #convert-btn:hover{
    color: #fff;
  background-color: #93ddff;
  border-color: #93ddff;
  }  

  h3{
    margin-top: 20px;
  }
  </style>
  