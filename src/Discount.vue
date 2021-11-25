<template>
    <div class="discount">
        <h4 >지금 결제하면 {{할인율}}% 할인</h4>
    </div>
</template>

<script>
export default {
    name:'Discount',
    data(){
        return{
            할인율 : 5,
        }
    },
    updated(){
        if(this.할인율==-1){
            alert('할인마감');
            this.$emit('discountend');
        }
        
    },

    mounted(){
        let interval = setInterval(()=>{
            if(this.할인율==0) {
                clearInterval(interval);
                
            }
            this.할인율=this.할인율-1;
            
        },1000);
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