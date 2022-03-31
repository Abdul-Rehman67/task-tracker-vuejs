<template>
<div :key="task.id" v-for="item in task">
<!-- <h3>{{item.text}}</h3 -->
<SingleTask :task="item" @delete-task="$emit('delete-task',item.id)" @toggle-reminder="$emit('toggle-reminder',item.id)"/>


</div>
  
</template>

<script>
import SingleTask from './SingleTask.vue'
export default {
    name:"Task",

    props:{
        task:{
            type:Array
        }

    },
    components:{
        SingleTask,
    },
    // emits:['delete-task','toggle-reminder ']

}
</script>

<style>

</style>