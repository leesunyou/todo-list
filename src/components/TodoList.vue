<template>
<ul>
  <li v-for="(todoItem,index) in propsdata" :key="todoItem"><span class="bullet"></span>{{todoItem}} <button class="del" @click="removeTodo(todoItem,index)">삭제</button></li>
</ul>
</template>

<script>
export default {
  props: ['propsdata'],
  methods: {
    removeTodo(todoItem, index){
      this.$emit('removeTodo', todoItem,index);
    }
  }
}
</script>

<style>
ul {
  list-style-type: none;
  padding: 1em;
  margin-bottom: 20px;
  text-align: left;
}

li {
  padding: 5px;
}

.bullet {
  display: inline-block;
  width: 1em;
  height: 1em;
}

.del {
  width: 20px;
  margin-left: 5px;
  text-indent: -9999px;
  background: url(../assets/delete.png) center/12px no-repeat;
}
</style>