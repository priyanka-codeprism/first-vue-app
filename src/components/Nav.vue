<template>
    <header>
        <h1>{{title}} </h1>
        <Button v-show='homepage'  
        :color='showAddTask ?"red" :"green" '
        @toogle-add-task="$emit('toogle-add-task')"
        />
    </header>
</template>
<script>
import Button from './Button.vue'
export default{
    name:'Nav',
    props:{
        title:String,
         showAddTask:Boolean
        },
    //or you can use
    //props:{
    //    title:String,
    //}
    //if you want default value (if you dont pass any prop then it will shhow the default value)
    //props:{
    //    title:{
    //          type:String,
    //           default:'hello world'
   // }
    //}
    components:{ Button},
    computed:{
        homepage(){
            if(this.$route.path==='/'){
                return true;
            }else{
                return false
            }
        }
    }
   
    //  emits:['toogle-add-task']
}
</script>
<style>
header{
    display: flex;
    align-items: center;
    justify-content: space-between;
    }
</style>