<template>

  <Transition name="fade">
    <Modal @closeBtn = "모달창열렸니 = false;" :원룸들= "원룸들" :누른버튼="누른버튼" :모달창열렸니="모달창열렸니" />
  </Transition>

  <!-- <div class="black-bg" v-if="모달창열렸니 == true">
    <div class="white-bg">
        <h4>{{원룸들[누른버튼].title}}</h4>
        <img :src="원룸들[누른버튼].image" style="width : 50%">
        <p>{{원룸들[누른버튼].content}}</p>
        <p>가격 : {{원룸들[누른버튼].price}}원</p>
        <Discount/>
        <button @click="모달창열렸니 = false">닫기</button>
    </div>
  </div> -->

  <div class="menu">
    <a v-for="a in 메뉴들" :key="a">{{ a }}</a>
  </div>

  <Discount v-if="showDiscount == true"/>

  <button @click="priceSort">가격순</button>
  <button @click="priceRSort">가격역순</button>
  <button @click="nameSort">상품명 가나다순</button>
  <button @click="sortBack">되돌리기</button>

  <!-- <img alt="Vue logo" src="./assets/logo.png"> -->
  <!-- <div v-for="(a,i) in products" :key="i">
    <h4>{{a}}</h4>
    <p>50 만원</p>tjdn
  </div> -->

  <Card @openModal="모달창열렸니 = true; 누른버튼 = $event" :원룸="원룸들[i]" v-for="(작명,i) in 원룸들" :key="작명"/>
  <!-- <Card :원룸="원룸들[1]"/>
  <Card :원룸="원룸들[2]"/>
  <Card :원룸="원룸들[3]"/>
  <Card :원룸="원룸들[4]"/> -->



<!--   
  <div v-for="(a,i) in 원룸들" :key="a">
    <img :src="원룸들[i].image" class="room-img">
    <h4 @click ="모달창열렸니 = true; 누른버튼 = i">{{원룸들[i].title}}</h4>
    <p>{{원룸들[i].price}}원</p>
  </div> -->
  
  
</template>

<script>

import data from './assets/oneroom.js';
import Discount from './Discount.vue';
import Modal from './Modal.vue';
import Card from './Card.vue';


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
      원룸들오리지널 : [...data],
      showDiscount : true,
    }
  },
  methods :{
    increase(i){
      this.신고수[i]++;
    },
    priceSort(){
      this.원룸들.sort(function(a,b){
        return a.price-b.price;
      });
    },
    priceRSort(){
      this.원룸들.sort(function(a,b){
        return b.price-a.price;
      });
    },
    nameSort(){
      this.원룸들.sort(function(a,b){
        return a.title.localeCompare(b.title);
      });
    },
    sortBack(){
      this.원룸들 = [...this.원룸들오리지널];
    },  
    
  },

  components: {
    Discount : Discount,
    Modal : Modal,
    Card : Card,
  },

  // mounted() {  // lifecycle hook
  //   setTimeout(() => {
  //     this.showDiscount = false;
  //   }, 2000);

  // },

  
  
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

.fade-enter-from{
  transform: translateY(-1000px);
}

.fade-enter-active{
  transition: all 1s;
}

.fade-enter-to{
  transform: translateY(0px);
}


.fade-leave-from{
  opacity: 1;
}

.fade-leave-active{
  transition: all 1s;
}

.fade-leave-to{
  opacity: 0;
}


</style>
