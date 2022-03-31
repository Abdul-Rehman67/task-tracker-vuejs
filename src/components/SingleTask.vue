<template>
  <div
  @dblclick="$emit('toggle-reminder',task.id)"
  
   :class="[task.remainder ? 'reminder' : '', 'task']">
    <h3>
      {{ task.text }}
      <i @click="onDelete(task.id)" class="fas fa-times"></i>
    </h3>
    <p>{{ task.day }}</p>
  </div>
</template>

<script>
export default {
  name: "SingleTask",
  props: {
    task: {
      type: Object,
    },
  },

  methods: {
    onDelete(id) {
      console.log("id====>", id);
      this.$emit("delete-task", id);
    },
  },
};

// console.log("task===>",task);
</script>

<style scoped>
.fas {
  color: red;
}

.task {
  background: #f4f4f4;
  margin: 5px;
  padding: 10px, 5px;
  cursor: pointer;
}
.task h3 {
  display: flex;
  align-items: center;
  justify-content: space-between;
}
.task.reminder {
  border-left: 5px solid green;
}
</style>
