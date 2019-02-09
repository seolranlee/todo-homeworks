<template>
  <ul class="todo-list">
    <li v-for="todo in todos">
      <todo-item
        :todo="todo"
        v-on:onCheck="onCheck"
        v-on:onRemove="onRemove"
      />
    </li>
  </ul>
</template>

<script>

  import TodoItem from './TodoItem';

  export default {
    props: ['todos'],
    components: {
      'todo-item': TodoItem,
    },
    name: "TodoList",
    methods: {
      onCheck(id){
        this.$emit('onCheck', id);
      },
      onRemove(id){
        // alert('remove');
        // 질문
        this.$emit('onRemove',id);
      }
    }

  }
</script>

<style scoped>

</style>
