<template>
  <div class="input_box">
    <input type="text" placeholder="할 일을 입력하세요." v-model="newTodoItem" @keyup.enter="addTodo">
    <button class="add" @click="addTodo">추가</button>
  </div>
</template>

<script>
export default {
    data(){
    return{
      newTodoItem:''
    }
  },
  methods:{
    addTodo(){
      if(this.newTodoItem !== ''){
        const value = this.newTodoItem && this.newTodoItem.trim();
        this.$emit('addTodo',value);
        this.newTodoItem='';
      }
    }
  }
}
</script>

<style>
.input_box {
  height: 50px;
  border-radius: 5px;
  margin: 30px 0;
  background: #fff;
}

input {
  width: 85%;
  height: 100%;
  border-radius: 5px 0 0 5px;
  padding: 15px;
  background: transparent;
  font-size: 1rem;
}

input:focus {
  outline: none;
}

.add {
  width: 15%;
  height: 100%;
  border-radius: 0 5px 5px 0;
  background: #ddd url(../assets/add.png) center/20px no-repeat;
  text-indent: -9999px;
  transition: .2s;
}

.add:hover,
.add:focus {
  background: #ccc url(../assets/add.png) center/20px no-repeat;
}
</style>