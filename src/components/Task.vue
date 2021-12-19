<template>
    <div v-for="(ele,index) in tasks" :key="index">
        <SingleTask  @delete-task="$emit('delete-task', ele.id)"
          @toggle-reminder="$emit('toggle-reminder',ele.id)" 
          :task='ele'/>
    </div>
</template>
<script>
import SingleTask from './SingleTask.vue'
export default {
    name:'Task',
    props:{
        tasks:Array
    },
     components:{SingleTask},
     emits:['delete-task','toggle-reminder']
}
</script>
