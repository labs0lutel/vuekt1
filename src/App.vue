<template>
  <div>
    <AddForm @addTodo="addTodo" />
    <TodoList 
      :todos="todos" 
      @changeTodos="changeTodos" 
      @deleteTodoByid="deleteTodoByid" 
    />
  </div>
</template>

<script>
import { ref } from 'vue';
import AddForm from './components/AddForm.vue';
import TodoList from './components/TodoList.vue';

export default {
  components: {
    AddForm,
    TodoList,
  },
  setup() {
    const startTodos = [
      { id: 1, title: 'Помыть руки', completed: true },
      { id: 2, title: 'Сделать зарядку', completed: false },
      { id: 3, title: 'Наконец изучить React', completed: true },
    ];

    const todos = ref(startTodos);

    const addTodo = (title) => {
      const newTodo = { id: Date.now(), title, completed: false };
      todos.value.push(newTodo);
    };

    const deleteTodoByid = (id) => {
      todos.value = todos.value.filter((todo) => todo.id !== id);
    };

    const changeTodos = (id) => {
      const todo = todos.value.find((todo) => todo.id === id);
      if (todo) {
        todo.completed = !todo.completed;
      }
    };

    return { todos, addTodo, deleteTodoByid, changeTodos };
  },
};
</script>
