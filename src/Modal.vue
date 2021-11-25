<template>
    <div class="black-bg" v-if="모달창열렸니==true">
        <div class="white-bg">
            <h3>상세페이지입니다</h3>
            <h4>{{원룸들[clicks].title}}</h4>
            <p>{{원룸들[clicks].content}}</p>
            <!--<input @input="개월 = $event.target.value">-->
            <input v-model ="개월">
            <select v-model ="개월">
                <option>1</option>
                <option>3</option>
                <option>6</option>
                <option>12</option>
                <option>24</option>
            </select>

            <button @click="$emit('closeModal')">닫기창</button> 
            <p>{{개월}}개월 선택함 : {{원룸들[clicks].price * 개월}}원</p>
        </div>
  </div>
</template>

<script>
export default {
    name:'Modal',
    data(){
        return{
            개월 : 1,
        }
    },
    watch : {
        개월(){
            return this.개월 = this.개월.replace(/[^0-9]/g, '');
        }
    },
    props:{
        원룸들:Array,
        clicks:Number,
        모달창열렸니:Boolean,
    }
}
</script>

<style >
.discount{
    background:#eee;
    padding :10px;
    margin : 10px;
    border-radius:5px;
}
</style>

