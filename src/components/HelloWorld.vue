<template>
  <div class="hello">
    <input v-model.number="operand1" />
    <input v-model.number="operand2" />
    ={{ result }}
    <div>
      <button @click="operations('+')">+</button>
      <button @click="operations('-')">-</button>
      <button @click="operations('*')">*</button>
      <button @click="operations('/')">/</button> 
      <button @click="operations('%')">%</button>
    </div>
    <div>
      <input v-model.number="operand3"/>
      <input v-model.number="pow"/>
     = {{resPow}}
    </div>
    <div>
      <button @click="operations('**')">**</button> 
      
    </div>
  </div>
</template>

<script>
export default {
  data: () => ({
    operand1: null,
    operand2: null,
    operand3 : null,
    pow: null,
    result: null,
    resPow: null,
   
  }),

  props: {},
  methods: {
    // sum(){
    //   this.result = this.operand1 + this.operand2
    // },
    // sub(){this.result = this.operand1 - this.operand2
    // },
    // mul(){
    //   this.result = this.operand1 * this.operand2
    // },
    // div(){
    //   this.result = this.operand1 / this.operand2
    // }
 operations: function (operator) {
      switch (operator) {
        case '+':
          this.result = +this.operand1 + +this.operand2;
          break;
        case "-":
          this.result = +this.operand1 - +this.operand2;
          break;
        case "/":
          this.result = +this.operand1 / +this.operand2;
          break;
        case "*":
          this.result = +this.operand1 * +this.operand2;
          break;
        case"**":
        this.resPow= this.operand3 ** +this.pow;
        break;
        case "%":
          this.result= +this.operand1 % +this.operand2;
        default:
          this.result = "invalid operator";

      }
    }
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
