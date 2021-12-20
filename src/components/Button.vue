<template>
    <button class='btn' @click="onClick()" :style='{background:color}'>{{text}}</button>
</template>
<script>
export default{
    name:'Button',
    props:{
        text:String,
        color:String,
    },
    methods:{
        onClick(){
            console.log('click')
            this.$emit('toogle-add-task',)
        }
    }
}
</script>
<style>
.btn{
    color:white;
    padding:10px 20px;
}
</style>