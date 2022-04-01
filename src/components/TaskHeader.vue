<template>
  <header>
    <h1>{{ title }}</h1>
    <ButtonComp :text="showAddTaskP ? 'Close':'Add Task'"  @AddTaskToggle="$emit('AddTaskToggle')"/>
  </header>
</template>

<script>
import ButtonComp from './ButtonComp.vue'
export default {
  name: "TaskHeader",
  props: {
    title: {
      type: String,
    },
    showAddTaskP:{
      type:Boolean
    }
    
  },
  components:{
    ButtonComp,
  },

};
</script>
<style scoped>
header {
  display: flex;
  justify-content: space-around;
  align-items: center;
  margin-bottom: 20px;
}
</style>
