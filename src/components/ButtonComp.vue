<template>
  <button type="button" @click="addTask" class="btn btn-primary">
    {{ text }}
  </button>
</template>

<script>
export default {
  name: "ButtonComp",
  props: {
    text: {
      type: String,
    },
  },
  methods: {
    addTask () {
        console.log("hello");
    },
  },
};
</script>
