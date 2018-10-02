<template>
  <div id="app">
    <TodoHeader></TodoHeader>
    <TodoInput v-on:addTodo="addTodo"></TodoInput>
    <TodoList v-bind:propsdata="todoItems" @removeTodo="removeTodo"></TodoList>
    <TodoFooter v-on:removeAll="clearAll"></TodoFooter>
  </div>
</template>

<script>
// var TodoHeader = {
//   template: '<div>header</div>'
// };
// var TodoInput = {
//   template: '<div>input</div>'
// };
// var TodoList = {
//   template: '<div>list</div>'
// };
// var TodoFooter = {
//   template: '<div>footer</div>'
// };

// 싱글 파일 컴포넌트 체계(.vue 파일 체계)
// 특정 컴포넌트에서 다른 위치에 있는 컴포넌트의 내용을 불러올 때 쓰이는 ES6 import 구문
import TodoHeader from './components/TodoHeader.vue'
import TodoInput from './components/TodoInput.vue'
import TodoList from './components/TodoList.vue'
import TodoFooter from './components/TodoFooter.vue'

export default {
  data(){
    return{
      todoItems: []
    }
  },
  created(){
    if (localStorage.length>0){
      for (var i=0; i<localStorage.length; i++){
        this.todoItems.push(localStorage.key(i));
      }
    }
  },
  methods:{
    addTodo(todoItem){
      localStorage.setItem(todoItem, todoItem);
      this.todoItems.push(todoItem);
    },
    removeTodo(todoItem, index){
      localStorage.removeItem(todoItem);
      this.todoItems.splice(index, 1);
    },
    clearAll(){
      localStorage.clear();
      this.todoItems = [];
    }
  },
  components: {
    'TodoHeader': TodoHeader,
    'TodoInput': TodoInput,
    'TodoList': TodoList,
    'TodoFooter': TodoFooter
  }
}
</script>

<style>
  body {
    text-align: center;
    background-color: #f6f6f8;
  }
  button {
    border-style: groove;
  }
  .shadow {
    box-shadow: 5px 10px 10px rgba(0,0,0,0.03)
  }
</style>
