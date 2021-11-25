<template>



<transition name="fade">
  <Modal @closeModal="모달창열렸니=false" :원룸들="원룸들" :clicks="누른거" :모달창열렸니="모달창열렸니" />
</transition>

  <div class="menu">
    <a v-for="작명 in 메뉴" :key="작명"> {{ 작명 }}</a>
  </div>

<discntbanner v-if="showDiscount==true" @discountend="showDiscount=false" />
<button @click="priceSort">가격순정렬</button>
<button @click="sortBack">되돌리기</button>
<Card @openModal="모달창열렸니=true;누른거=$event" v-for ="(a,i) in 원룸들" :a="a"  :key="i"/>


<!--Card :원룸="원룸들[i]" v-for ="(작명,i) in 원룸들"  :key="i"/>-->

  <!--<div v-for = "(a,i) in 원룸들" :key = "i">
    <img :src="a.image" class="room-img">
    <h4 @click="모달창열렸니=true; 누른거=i;"  class="red" :style="스타일">{{원룸들[i].title}}</h4>
    <p>{{원룸들[i].price}}원 </p>
    <button @click="increase(i)">허위매물신고</button> <span>신고수 : {{신고수[i]}}</span>
  </div>
  -->

  <!--<div>
    <img alt = "room0" src="./assets/room0.jpg" class="room-img"> 
    <h4 @click="모달창열렸니=true"  class="red" :style="스타일">{{products[0]}}</h4>
    <p>{{price[0]}} 만원</p>
    <button @click="increase(0)">허위매물신고</button> <span>신고수 : {{신고수[0]}}</span>
  </div>

  <div>
    <h4>{{products[1]}}</h4>
    <p>{{price[1]}} 만원</p>
    <button @click="increase(1)">허위매물신고</button> <span>신고수 : {{신고수[1]}}</span>
  </div>

  <div>
    <h4>{{products[2]}}</h4>
    <p>{{price[2]}} 만원</p>
    <button @click="increase(2)">허위매물신고</button> <span>신고수 : {{신고수[2]}}</span>
  </div>-->
  
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
      showDiscount:true,
      오리지널원룸:[...data],
      누른거 : 0,
      원룸들 : data,
      모달창열렸니 : false,
      신고수:[0,0,0,0,0,0],
      price:['70만원', '60만원', '50만원'],
      스타일: 'color:blue',
      products:['역삼동원룸', '천호동원룸','마포구원룸'],
      메뉴:['Home', 'Shop','About'] 
    }
  },
  methods : {
    increase(i){
      this.신고수[i] +=1;
    },
    sortBack(){
      this.원룸들=[...this.오리지널원룸];
    },
    priceSort(){
      this.원룸들.sort(function(a,b){
        return a.price-b.price
      })
    },
  },
  components: {
    discntbanner:Discount,
    Modal:Modal,
    Card:Card,
  }
}
</script>

<style>
.fade-leave-from{
  opacity:1;
  
}
.fade-leave-active{
  transition: all 1s;
}
.fade-leave-to{
  opacity:0;
}

.fade-enter-from{
  opacity:0;
  
}
.fade-enter-active{
  transition: all 1s;
}
.fade-enter-to{
  opacity:1;
}

body{
  margin : 0
}
div {
  box-sizing: border-box;
}
.black-bg{
  width:100%;height:100%;
  background:rgba(0,0,0,0.5);
  position:fixed;padding:20px;
}
.white-bg{
  width:100%;background: white;
  border-radius:8px;
  padding:20px;
}

.room-img{
  width:100%;
  margin-top:40px;
}
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
.menu{
  background:darkslateblue;
  padding : 15px;
  border-radius: 5px;
}
.menu a {
  color: white;
  padding : 10px;
}
</style>
