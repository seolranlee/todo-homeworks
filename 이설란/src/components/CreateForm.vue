<template>
  <div>
    <form v-on:submit.prevent="onSubmit">
      <input value="input" type="text" v-model="input">
      <button type="submit">입력</button>
    </form>
  </div>
</template>

<script>
  export default {
    name: "CreateForm",
    data () {
      return {
        input: '',
      }
    },
    methods: {
      onSubmit(){
        if (this.input===''){
          alert('할 일을 입력하세요.');
          return false;
        }
        this.$emit('update', this.input);
        this.input = '';
      }
    },
  }
</script>

<style scoped>

</style>
