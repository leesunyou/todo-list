<template>
  <div>
    <TodoHeader />
    <TodoInput @addTodo="addTodo" />
    <TodoList :propsdata="todoItems" @removeTodo="removeTodo" />
    <TodoFooter @removeAll="clearAll" />
  </div>
</template>

<script>
import TodoHeader from './components/TodoHeader.vue'
import TodoInput from './components/TodoInput.vue'
import TodoList from './components/TodoList.vue'
import TodoFooter from './components/TodoFooter.vue'

export default {
    data(){
    return {
      todoItems: []
    }
  },

  methods: {
    addTodo(todoItem){
      localStorage.setItem(todoItem,todoItem);
      this.todoItems.push(todoItem);
    },

    removeTodo(todoItem,index){
      localStorage.removeItem(todoItem);
      this.todoItems.splice(index,1);
    },

    clearAll(){
      localStorage.clear();
      this.todoItems=[];
    }
  },

  created(){
    if(localStorage.length > 0){
      for(let i=0;i<localStorage.length; i++){
        this.todoItems.push(localStorage.key(i));
      }
    }
  },

  components: {
    'TodoHeader' : TodoHeader,
    'TodoInput' : TodoInput,
    'TodoList' : TodoList,
    'TodoFooter' : TodoFooter
  }
}
</script>

<style>
@import url('https://fonts.googleapis.com/css2?family=Noto+Sans+KR&display=swap');

*{
  margin:0;
  padding:0;
  box-sizing: border-box;
}

html {
  overflow-x: hidden;
}

body {
  background: #333;
  color: #fff;
  font-family: 'Noto Sans KR', sans-serif;
  text-align: center;
}

#app {
  width: 80%;
  margin: 0 auto;
  padding: 50px 0;
}

input, button {
  border: none;
}

button {
  cursor: pointer;
}
</style>