<template>
    <ul class="todo-main">
        <Item 
          :key="todosObj.id" 
          v-for="todosObj in todos" 
          :todosObj="todosObj"
          :delTodo="delTodo"
          :updateTodo="updateTodo"
        ></Item>
    </ul>
</template>

<script>
    import Item from './item'
    export default {
      name:'List',
      components:{Item},
      // 声明接受props
      props:{
        todos:{
          type:Array,
          required:true,
        },
        delTodo:{
          type:Function,
          required:true,
        },
        updateTodo:{
          type:Function,
          required:true
        }
      }
    }
</script>

<style>
  /*main*/
.todo-main {
  margin-left: 0px;
  border: 1px solid #ddd;
  border-radius: 2px;
  padding: 0px;
}

.todo-empty {
  height: 40px;
  line-height: 40px;
  border: 1px solid #ddd;
  border-radius: 2px;
  padding-left: 5px;
  margin-top: 10px;
}
</style>