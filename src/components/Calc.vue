<template>
  <div>
    <div>
      <input class="input" type="number" placeholder="op1" v-model.number="operand1" />
      <input class="input" type="number" placeholder="op2" v-model.number="operand2" />
    </div>
    <div class="error" v-if="error">
        Ошибка: {{ error }}
    </div>

    <div class="buttons">
        <button class="btn" v-for="btn in buttons" 
                :key="btn"
                v-bind:title="btn"
                @click="calculate(btn)"
        >
                {{ btn }}
        </button>
    </div>
    <!-- <div class="btns">
      <button class="btn" @click="add">+</button>
      <button class="btn" @click="substract">-</button>
      <button class="btn" @click="multiply">*</button>
      <button class="btn" @click="divide">/</button>
      <button class="btn" @click="divideRound">round</button>
      <button class="btn" @click="pow">pow</button>
    </div> -->
    <div class="result">
    result : {{ result }}
    </div>

    <div class="check">
        <input type="checkbox" id="checkbox" v-model="checked">
            {{ checked }}
    </div>

     <div class="keyboard">
        <button class="key" v-for="key in keyboard"
            :key="key"
            :v-bind:title="key"
            >
                {{ key }}
        </button>
    </div>

    <div class="collection">
        <div v-for="(item, idx) in collection" :key="idx">
            {{ idx }} - {{ item }}
        </div>
    </div>

    <div class="radio">
        <input type="radio" value="Операнд №1" v-model="radio1">
        <label>Операнд №1</label>
        <input type="radio" value="Операнд №2" v-model="radio2">
        <label>Операнд №2</label>
    </div>
  </div>
</template>

<script>
export default {
  name: "Calc",
  data:()=>({
    operand1: 0,
    operand2: 0,
    result: 0,
    buttons: ['+','-','*','/','round', 'pow'],
    keyboard: [1,2,3,4,5,6,7,8,9,0],
    error: "",
    checked: "Отобразить экранную клавиатуру",
    radio1: "",
    radio2: ""
    }),

  methods: {
      calculate(op){
        const calcOperations = {
            '+': ()=> this.operand1 + this.operand2,
            '-': ()=> this.operand1 - this.operand2,
            '*': ()=> this.operand1 * this.operand2,
            '/': ()=> this.operand1 / this.operand2,
            'round': ()=> Math.round(this.operand1 / this.operand2),
            'pow': ()=> Math.pow(this.operand1, this.operand2)
        }
            this.result = calcOperations[op]()
        },
  }
}
</script>

<style lang="scss" scoped>
.error {
    color: red
}

.buttons {
    margin-top: 20px;
    margin-bottom: 20px;
}

.btn {
    font-size: 14px;
	text-align: center;
	letter-spacing: 0.04em;
	color: #FFFFFF;
	background: rgb(93, 99, 104);
	box-shadow: 5px 10px 10px rgba(107, 110, 114, 0.2);
	border-radius: 3px;
	padding: 5px;
    text-decoration: none;
    min-width: 40px;
    margin-right: 5px;
}

.result {
    color: cadetblue;
    font-size: 18px;
    font-weight: 700;
    text-align: center;
}

.input{
    text-align: center;
    border: 2px solid gray;
    border-radius: 3px;
    box-shadow: 5px 10px 10px rgba(173, 177, 182, 0.3);
    margin-right: 5px;
    padding: 5px;
    width: 150px;
}

.key{
    background-color: cadetblue;
    margin-right: 5px;
    color: #FFFFFF;
    font-size: 16px;
    font-weight: 700;
}

.check{
    margin-block: 20px;
}
.radio {
    margin-top: 20px;
    font-weight: 700;
}

.radio label{
    margin-right: 20px;
}

</style>