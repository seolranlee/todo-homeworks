<template>
  <div class="todo-item"
       :class="[ todo.checked===false ? '' : 'active']">
    <div class="check">&#10004;</div>
    <div class="txt" @click="onCheck">{{todo.text}}</div>
    <div class="remove" @click="onRemove">[지우기]</div>
  </div>
</template>

<script>
  export default {
    props: ['todo'],
    name: "TodoItem",
    data(){
      return {}
    },
    methods: {
      onCheck(){
        this.$emit('onCheck', this.todo.id);
      },
      onRemove(e){
        e.stopPropagation();
        this.$emit('onRemove', this.todo.id);
      }
    }
  }
</script>

<style scoped>
  .todo-item{
    display: flex;
  }
  .todo-item .txt{cursor: pointer}
  .todo-item .remove{cursor: pointer}
  .todo-item .check{
    opacity: 0;
  }
  .todo-item.active .check{
    opacity: 1;
  }
  .todo-item.active .txt{
    text-decoration: line-through;
  }
  .todo-item .txt{flex: 1}
</style>
