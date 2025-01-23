<template>
  <div 
      class="todo_card"
      :style="{ backgroundColor: completed ? 'green' : 'red' }"
      @click="changeTodos"
      @dblclick="deleteTodoByid">
    
      <h2>{{ title }}</h2>
  </div>
</template>
  
  <script>
  export default {
    props: {
      id: Number,
      title: String,
      completed: Boolean,
    },
    methods: {
      changeTodos() {
        this.$emit('changeTodos', this.id);
      },
      deleteTodoByid() {
        this.$emit('deleteTodoByid', this.id);
      },
    },
  };
</script>
  