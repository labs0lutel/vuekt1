<template>
  <div>
      <TodoItem
        v-for="todo in todos"
        :key="todo.id"
        :id="todo.id"
        :title="todo.title"
        :completed="todo.completed"
        @changeTodos="changeTodos"
        @deleteTodoByid="deleteTodoByid"/>
      
  </div>
</template>
  
<script>
  import TodoItem from './TodoItem.vue';
  
  export default {
    components: {
      TodoItem,
    },
    props: {
      todos: Array,
    },
    methods: {
      changeTodos(id) {
        this.$emit('changeTodos', id);
      },
      deleteTodoByid(id) {
        this.$emit('deleteTodoByid', id);
      },
    },
  };
</script>
  