<script>
export default {
  data() {
    return {
      output: null, //누른 애들 출력되는 곳
      prev: null, //이전에 내가 누른값
      cur: null,
      operator: null,
    }
  },

  methods: {
    operation(event) {

      const number = event.currentTarget.value;

      if(['+','-','*','/','='].includes(number)){
        //연산로직 구현
        this.output = null;   // 출력값을 초기화
        this.operator = number;   // 현재 연산자를 저장
        this.prev = Number(this.cur);  // 현재 값을 이전 값으로 저장 (숫자로 변환)
        this.cur = null;   // 현재 값을 초기화
 
        return;
      }

      //사용자가 입력한 숫자(실제로는 문자열) 저장
      //=> output부분에 누른 값 텍스트 띄우기
      this.cur = this.cur === null?number:(this.cur+=number);
      //입력한 값이 출력칸(output)에 표시되도록 output 데이터에 저장
      this.output = this.cur;

      if(this.prev != null){

        this.cur = Number(this.cur);

        switch(this.operator){
          case '+':
            this.output = this.prev + this.cur;
            break;
          
        }


      }



    },
  },

}
</script>

<template>
      <div class="calculator">
        <form name="forms">
          <input v-model="output" type="text" name="output" readonly />
          <input type="button" class="clear" value="C" @click="operation"/>
          <input type="button" class="operator" value="/" @click="operation"/>
          <input type="button" value="1" @click="operation"/>
          <input type="button" value="2" @click="operation"/>
          <input type="button" value="3" @click="operation"/>
          <input type="button" class="operator" value="*" @click="operation"/>
          <input type="button" value="4" @click="operation"/>
          <input type="button" value="5" @click="operation"/>
          <input type="button" value="6" @click="operation"/>
          <input type="button" class="operator" value="+" @click="operation"/>
          <input type="button" value="7" @click="operation"/>
          <input type="button" value="8" @click="operation"/>
          <input type="button" value="9" @click="operation"/>
          <input type="button" class="operator" value="-" @click="operation"/>
          <input type="button" class="dot" value="." @click="operation"/>
          <input type="button" value="0" @click="operation"/>
          <input type="button" class="operator result" value="=" @click="operation"/>
        </form>
    </div>
</template>

<style scoped>
  @import './assets/style.css';
</style>