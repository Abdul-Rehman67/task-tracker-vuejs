<template>
  <header>
    <h1>{{ title }}</h1>
    <ButtonComp text = "Add Task"/>
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
