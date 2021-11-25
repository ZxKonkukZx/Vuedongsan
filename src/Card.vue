<template>
    <div>
        <img :src="a.image" class="room-img">
        <h4 @click="$emit('openModal',a.id)"  class="red" :style="스타일">{{a.title}}</h4>
        <p>{{a.price}}원 </p>
        <!--<button @click="increase(i)">허위매물신고</button> <span>신고수 : {{신고수[i]}}</span>-->
  </div>
</template>


<script>
export default {
    name:'Modal',
    props:{
        a:Array,
        clicks:Number,
        모달창열렸니:Boolean,
    }
}
</script>
