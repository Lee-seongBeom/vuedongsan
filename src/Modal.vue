<template>
  <div class="black-bg" v-if="모달창열렸니 == true">
    <div class="white-bg">
      <img :src="원룸들[누른버튼].image" style="width : 50%">
        <h4>{{원룸들[누른버튼].title}}</h4>
        <p>{{원룸들[누른버튼].content}}</p>
        <p>가격 : {{원룸들[누른버튼].price}}원</p>
        <Discount/>
        <!-- <button @click="모달창열렸니 = false">닫기</button> -->
    </div>
  </div>
</template>

<script>
export default {
    name : 'Modal',
    props : {
      원룸들 : Array,
      누른버튼 : Number,
      모달창열렸니 : Boolean,
    },
}
</script>

<style>

</style>