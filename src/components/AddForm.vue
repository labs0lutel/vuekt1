<template>
    <div class="input_elem">
      <input @keyup.enter="handleKeyUp" />
    </div>
</template>
  
<script>
  export default {
    methods: {
      handleKeyUp(event) {
        this.$emit('addTodo', event.target.value);
        event.target.value = ''; 
      },
    },
  };
</script>
  