<template>
  <!-- <div v-if="1 == 2">
    안녕
  </div>
  <div v-else-if="3 ==3">
    안녕 elseif
  </div>
  <div v-else>
    안녕 else
  </div> -->


  
  <Modal/>

  <div class="black-bg" v-if="모달창열렸니 == true">
    <div class="white-bg">
        <h4>{{원룸들[누른버튼].title}}</h4>
        <img :src="원룸들[누른버튼].image" style="width : 50%">
        <p>{{원룸들[누른버튼].content}}</p>
        <p>가격 : {{원룸들[누른버튼].price}}원</p>
        <Discount/>
        <button @click="모달창열렸니 = false">닫기</button>
    </div>
  </div>

  <div class="menu">
    <a v-for="a in 메뉴들" :key="a">{{ a }}</a>
  </div>

  <Discount/>

  <img alt="Vue logo" src="./assets/logo.png">
  <!-- <div v-for="(a,i) in products" :key="i">
    <h4>{{a}}</h4>
    <p>50 만원</p>
  </div> -->

  <div v-for="(a,i) in 원룸들" :key="a">
    <img :src="원룸들[i].image" class="room-img">
    <h4 @click ="모달창열렸니 = true; 누른버튼 = i">{{원룸들[i].title}}</h4>
    <p>{{원룸들[i].price}}원</p>
  </div>
  
</template>

<script>

import data from './assets/oneroom.js';
import Discount from './Discount.vue';
import Modal from './Modal.vue';

export default {
  name: 'App',
  data(){
    return{
      누른버튼 : 0,
      원룸들 : data,
      모달창열렸니 : false,
      메뉴들 : ['Home', 'Shop', 'About'],
      products : ['역삼동원룸', '천호동원룸', '마포구원룸'],
      priceRandom : '가격은아무거나',
      productsStyle : 'color : blue',
      신고수 : [0, 0, 0,],
    }
  },
  methods :{
    increase(i){
      this.신고수[i]++;
    },
    
  },

  components: {
    Discount : Discount,
    Modal : Modal,
  }
}
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}

.menu{
  background: darkslateblue;
  padding: 15px;
  border-radius: 5px;
}

.menu a{
  color: white;
  padding: 10px;
}

.room-img{
  width: 30%;
  margin-top: 40px;
}

body{
  margin: 0;
}

div{
  box-sizing: border-box;
}

.black-bg{
  width: 100%;
  height: 100%;
  background: rgba(0,0,0,0.5);
  position: fixed;
  padding: 20px;
}

.white-bg{
  width: 100%;
  background:  white;
  border-radius: 8px;
  padding: 20px;
}

.discount{
  background: gray;
  padding : 10px;
  margin : 10px;
  border-radius: 5px;

}
</style>
