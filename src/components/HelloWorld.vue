<template>
  <div class="hello">
    <input v-model.number="operand1"  />
    <input v-model.number="operand2" />
    ={{ result }}
    <div class="operator">
      <button @click="operations('+')">+</button>
      <button @click="operations('-')">-</button>
      <button @click="operations('*')">*</button>
      <button @click="operations('/')">/</button>
      <button @click="operations('%')">%</button>
    </div>
    <div class="operand">
      <input v-model.number="operand3" />
      <input v-model.number="pow" />
      = {{ resPow }}
    </div>
    <div>
      <button @click="operations('**')">**</button>
    </div>
    <div class="checkPanel">
      <input type="checkbox" @click="visible=!visible" id="check"/>
      <label class="laabelForPanel" for="check">Отобразить экранную клавиатуру.</label>
      <div v-show="visible" class="groupNumbers">
        <button  v-for="item in buttons" v-bind:key="item.id" >{{item.title}}</button>
         <button>&#8592;</button>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  data: () => ({
    operand1: null,
    operand2: null,
    operand3: null,
    pow: null,
    result: null,
    resPow: null,
    buttons: [
      {id:1,title:'0'},
      {id:2,title:'1'},
      {id:3,title:'2'},
      {id:4,title:'3'},
      {id:5,title:'4'},
      {id:6,title:'5'},
      {id:7,title:'6'},
      {id:8,title:'7'},
      {id:9,title:'8'},
      {id:10,title:'9'}
    ],
    visible : false,
  }),

  props: {},
  methods: {
    operations: function(operator) {
      switch (operator) {
        case "+":
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
        case "**":
          this.resPow = this.operand3 ** +this.pow;
          break;
        case "%":
          this.result = +this.operand1 % +this.operand2;
        default:
          this.result = "invalid operator";
      }
    },
   },
   clog(element){
     console.log(element.target.value)
   }
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

button {
  margin: 10px;
  width: 50px;
  height: 50px;
}
.operator {
  margin: 10px;
}

.groupNumbers {
  /* display: none; */
  
  margin-left: 10px;
}

.operand {
  margin: 10px;
}
</style>
