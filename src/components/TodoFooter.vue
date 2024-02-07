<template>
<footer>
  <button class="clear" @click="clearTodo">전체 삭제</button>
  <small>2024 &copy;SUNYOU's Todo List</small>
</footer>
</template>

<script>
export default {
    methods: {
    clearTodo(){
      this.$emit('removeAll');
    }
  }
}
</script>

<style>
.clear {
  padding:10px 20px;
  border-radius: 5px;
  background:#ddd;
  color:#000;
  font-weight: bold;
  transition: .2s;
}

.clear:hover,
.clear:focus {
  background:#ccc;
}

small {
  display: block;
  margin-top:30px;
  padding:30px;
  border-top:1px solid #fff;
}
</style>