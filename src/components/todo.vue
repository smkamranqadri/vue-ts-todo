<template>
  <div>
    <input type="text" v-model="todo.text">
    <button @click="handleTodo(todo.text)">
      +
    </button>
  </div>
</template>

<script lang="ts">
import Vue from 'vue';
import { Component, Prop } from 'vue-property-decorator';

@Component({})
export default class Todo extends Vue {
  @Prop({ type: Function }) addTodo: Function;
  @Prop({ type: Function }) editTodo: Function;
  @Prop({ type: Object }) todo: { text: string, index: number };

  handleTodo() {
    console.log('todo', this.todo);
    if (this.todo.index) return this.editTodo(this.todo.text, this.todo.index);
    this.addTodo(this.todo.text);
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>

</style>
