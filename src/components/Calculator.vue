<template>
  <div id="background"><!-- Main background -->

          <div id="result">{{current}}</div>

           <div id="main">
               <div id="first-rows">
                    <button @click="del" class="del-bg" id="delete">Del</button>
                   <button @click="perc" value="%" class="btn-style operator opera-bg fall-back">%</button>
                   <button @click="plus" value="+" class="btn-style opera-bg value align operator">+</button>
                   </div>

                 <div class="rows">
                   <button @click="appendd('7')" value="7" class="btn-style num-bg num first-child">7</button>
                   <button @click="appendd('8')" value="8" class="btn-style num-bg num">8</button>
                   <button @click="appendd('9')" value="9" class="btn-style num-bg num">9</button>
                   <button @click="minus" value="-" class="btn-style opera-bg operator">-</button>
                   </div>

                   <div class="rows">
                   <button @click="appendd('4')" value="4" class="btn-style num-bg num first-child">4</button>
                   <button @click="appendd('5')" value="5" class="btn-style num-bg num">5</button>
                   <button @click="appendd('6')" value="6" class="btn-style num-bg num">6</button>
                   <button @click="multiple" value="*" class="btn-style opera-bg operator">x</button>
                   </div>

                   <div class="rows">
                   <button @click="appendd('1')" value="1" class="btn-style num-bg num first-child">1</button>
                   <button @click="appendd('2')" value="2" class="btn-style num-bg num">2</button>
                   <button @click="appendd('3')" value="3" class="btn-style num-bg num">3</button>
                   <button @click="devide" value="/" class="btn-style opera-bg operator">/</button>
                   </div>

                   <div class="rows">
                   <button @click="appendd('0')" value="0" class="num-bg zero" id="delete">0</button>
                   <button @click="point" value="." class="btn-style num-bg period fall-back">.</button>
                   <button @click="equals" value="=" id="eqn-bg" class="eqn align">=</button>
                   </div>

               </div>

           </div>

</template>

<script>
export default {
  name: 'Calculator',
  data(){
    return{
      current:'0',
      previous: null,
      operation: null,
    }
  },
  methods:{
    appendd(number){
      this.current === '0' ? this.current = this.current.slice(1) + number : this.current += number;
    },
    del(){
      this.current = '0';
    },
    perc(){
      this.current /= 100;
    },
    point(){
      this.current.indexOf('.') >= 0 ? this.current : this.current += '.';
    },
    opStart(operation){
      this.previous = this.current;
      this.current = '0';
      this.operation = operation;
    },
    plus(){
      this.opStart('plus');
    },
    minus(){
      this.opStart('minus');
    },
    devide(){
      this.opStart('devide');
    },
    multiple(){
      this.opStart('multiple');
    },
    equals(){
      switch (this.operation) {
        case 'plus':
          this.current = parseInt(this.previous) + parseInt(this.current);
          break;
        case 'minus':
          this.current = parseInt(this.previous) - parseInt(this.current);
        break;
        case 'multiple':
          this.current = parseInt(this.previous) * parseInt(this.current);
          break;
        case 'devide':
          this.current = parseInt(this.previous) / parseInt(this.current);
        break;
      };
      this.operation= null;
      this.previous= null;

    },
  }
}
</script>

<style scoped>
body {
background:#777;
}

#background {
  width:300px;
  height:400px;
  background:gray;
  margin:50px auto;
  transition: all 2s ease;
}

button {
  border:0;
  color:#fff;
}

#result {
  display:block;
  font-family: sans-serif;
  width:230px;
  height:40px;
  margin:10px auto;
  text-align: right;
  border:0;
  background:#3b3535;
  color:#fff;
  padding-top:20px;
  font-size:20px;
  margin-left: 25px;
  outline: none;
  overflow: hidden;
  letter-spacing: 4px;
  position: relative;
  top:10px;
}

#result:hover {

  cursor: text;

}

#first-rows {
  margin-bottom: 20px;
  position: relative;
  top:10px;
}

.rows {
  width:300px;
  margin-top:10px;
}

#delete {
  width:110px;
  height:50px;
  margin-left:25px;
  border-radius:4px;
}

/* Aligning the division and dot button properly */
.fall-back {
  margin-left:3px !important;
}

/* Aligning the addition and equals to button properly */
.align {
  margin-left: 6px !important;
}

/* Button styling */
.btn-style {
  width:50px;
  height:50px;
  margin-left:5px;
  border-radius:4px;
}

.eqn {
  width:50px;
  height:50px;
  margin-left:5px;
  border-radius:4px;
}

.first-child {
margin-left:25px;
}


/* Adding background color to the number values */
.num-bg {
  background:#000;
  color:#fff;
  font-size:26px;
  cursor:pointer;
  outline:none;
  border-bottom:3px solid #333;
}

.num-bg:active {
  background:#000;
  color:#fff;
  font-size:26px;
  cursor:pointer;
  outline:none;
  box-shadow: inset 5px 5px 5px #555;
}

/*Adding background color to the operator values */
.opera-bg {
  background:#333;
  color:#fff;
  font-size:26px;
  cursor: pointer;
  outline:none;
  border-bottom:3px solid #555;
}

.opera-bg:active {
  background:#333;
  color:#fff;
  font-size:26px;
  cursor: pointer;
  outline:none;
  box-shadow: inset 4px 4px 4px #555;
}

/*Adding a background color to the delete button */
.del-bg {
  background:#24b4de;
  color:#fff;
  font-size:26px;
  cursor: pointer;
  outline:none;
  border-bottom:3px solid #399cb9;
}

.del-bg:active {
  background:#24b4de;
  color:#fff;
  font-size:26px;
  cursor: pointer;
  outline:none;
  box-shadow: inset 4px 4px 4px #399cb9;
}

/*Adding a background color to the equals to button */
#eqn-bg {
  background:#17a928;
  color:#fff;
  font-size:26px;
  cursor: pointer;
  outline:none;
  border-bottom:3px solid #1f7a29;
}

#eqn-bg:active {
  background:#17a928;
  color:#fff;
  font-size:26px;
  cursor: pointer;
  outline:none;
  box-shadow: inset 4px 4px 4px #1f7a29;
}

</style>
