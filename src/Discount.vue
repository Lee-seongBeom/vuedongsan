<template>
    <div class="discount">
        <h4>지금 결제하면 {{cnt}}% 할인</h4>
    </div>
</template>

<script>
export default {
    name: 'Discount',
    data(){
        return{
            cnt : 30,
        }
    },
    mounted() {
        setInterval(() => {
            if(this.cnt > 0){
                this.cnt --;
            }
            
        }, 1000);
    },
}


</script>

<style>

</style>
