<template>

<div class="container">
  <TaskHeader title="Task-Tracker"/>
  <TaskComp :task="tasks" @delete-task="deleteTask" @toggle-reminder="toggleRemainder"/>

  

</div>
</template>

<script>

import TaskHeader from './components/TaskHeader.vue'
import TaskComp from './components/TaskComp.vue'
export default {
  name: 'App',
  components: {
    TaskHeader,
    TaskComp,
    
  },
  data(){
    return{
      tasks:[]
    }
  },

     
  methods:{
    deleteTask(id){
      console.log("task id ===>",id);

     

  }, 
  toggleRemainder(id){
    console.log("Hello",id);
    this.tasks= this.tasks.map((item)=>item.id===id?{...item, remainder : !item.remainder }:item
    )

}


  },
  created(){
    this.tasks= [{
      id:1,
      text:"Meeting at school",
      day : "March 31",
      remainder:true,
    },{
      id:2,
      text:"Meeting at office",
      day : "March 15",
      remainder:false,
    },{
      id:3,
      text:"Meeting with client",
      day : "March 10  ",
      remainder:true,
    }]
  }
}
</script>

<style>

</style>
