<template>
    <div class="calculator">
      <div class="display">{{current || 0}}</div>
      <div @click="clear" class="btn">AC</div>
      <div @click="sign" class="btn">+/-</div>
      <div @click="percent" class="btn">%</div>
      <div @click="divide()" class="btn operator">÷</div>
      <div @click="append('7')" class="btn">7</div>
      <div @click="append('8')" class="btn">8</div>
      <div @click="append('9')" class="btn">9</div>
      <div @click="times()" class="btn operator">x</div>
      <div @click="append('4')" class="btn">4</div>
      <div @click="append('5')" class="btn">5</div>
      <div @click="append('6')" class="btn">6</div>
      <div @click="minus()" class="btn operator">-</div>
      <div @click="append('1')" class="btn">1</div>
      <div @click="append('2')" class="btn">2</div>
      <div @click="append('3')" class="btn">3</div>
      <div @click="add()" class="btn operator">+</div>
      <div @click="append('0')" class="zero btn">0</div>
      <div @click="dot()" class="btn">.</div>
      <div @click="equal()" class="btn operator">=</div>
    </div>
</template>

<script>
export default {
  data()
  {
    return{
      previous: null,
      current: "",
      operator: null,
      operatorClicked: false,
    }
},
methods: {
  clear(){
    this.current = '0';
  },
  sign(){
    this.current = this.current.charAt(0) ===  '-' ?
    this.current.slice(1) : `-${this.current}`;
  },
  percent(){
    this.current = `${parseFloat(this.current) / 100}`
  },
  append(number){
    this.current = `${this.current}${number}`;
  },
  dot(){
    if(this.current.indexOf('.') === -1){
      this.append('.');
    }
  },
  setPrevious()
  {
    this.previous = this.current;
    this.operatorClicked = true;
  },
  divide(){
    this.operator = (a ,b) => a / b;
  },
  times(){
    this.operator = (a ,b) => a * b;
  },
  minus()
  {
    this.operator = (a ,b) => a - b;
  },
  add(){  
    this.operator = (a ,b) => a + b;
  }
}
}
</script>

<style scoped>
.calculator{
  user-select: none;
  margin: 0 auto;
  max-width: 30rem;
  font-size: 3.5rem;
  display: grid;
  grid-template-columns: repeat(4 , 1fr);
  grid-auto-rows: 50px , auto;
}
.display{
  user-select: none;
  grid-column:  1 /5;
  color: #fff;
  background: rgb(136, 126, 126);
}
.zero{
  grid-column: 1/3;
}
.btn{
  user-select: none;
  cursor: pointer;
  background-color: #eee;
  border: 1px solid #999;
}
.operator{
  background-color:rgb(255, 196, 0);
  color: #fff;
}


</style>
