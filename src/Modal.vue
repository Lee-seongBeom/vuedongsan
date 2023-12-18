<template>
  <div class="black-bg" v-if="모달창열렸니 == true">
    <div class="white-bg">
      <img :src="원룸들[누른버튼].image" style="width : 50%">
        <h4>{{원룸들[누른버튼].title}}</h4>
        <p>{{원룸들[누른버튼].content}}</p>
        <!-- <input @input="month = $event.target.value"/> -->
        <input v-model.number="month" />
        <!-- <textarea v-model="month"></textarea> -->
        <!-- <select v-model="month">
          <option>1</option>
          <option>2</option>
          <option>3</option>
        </select> -->
        <!-- <input type="checkbox" v-model="month"/> -->

        <p>{{month}}개월 선택함 : {{원룸들[누른버튼].price + month}}원</p>
        <!-- <Discount/> -->
        <button @click="closeBtn">닫기</button>
    </div>
  </div>
</template>

<script>
export default {
    name : 'Modal',
    data(){
      return {
        month : '1',
      }
    },
    props : {
      원룸들 : Array,
      누른버튼 : Number,
      모달창열렸니 : Boolean,
    },
    methods: {
      closeBtn(){
        this.$emit('closeBtn', this.모달창열렸니)
      }
    },
    watch :{ // 감시자 느낌
      month(a){ //data명과 같게 추가
        // 사용자가 month를 글자로 입력하면 경고문 띄우기
        if(a >= 13){
          alert('13이상 입력하지 마셈');
          this.month = 1;
        }
        
        if(isNaN(a) == true){
          alert('문자 입력 금지');
          this.month = 1;
        }

      },
    }
}
</script>

<style>

</style>