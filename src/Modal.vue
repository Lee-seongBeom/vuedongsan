<template>
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
</template>

<script>
export default {
    name : 'Modal'
}
</script>

<style>

</style>