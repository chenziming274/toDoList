<template>
  <div class="todo-footer">
      <label>
        <input type="checkbox" :checked="isAll" @click="updataA"/>
      </label>
      <span>
        <span>已完成{{doneCount}}</span> / 全部{{total}}
      </span>
      <button class="btn btn-danger" @click="clearAllD">清除已完成任务</button>
  </div>
</template>

<script>
    export default {
      name:'Footer',
      methods: {
        updataA(event){
          this.updataAll(event.target.checked)
        },
        clearAllD(){
          this.clearAllDone()
        }
      },
      computed:{
        doneCount(){
          return this.todos.reduce((pre,current)=>pre + (current.done ? 1 : 0), 0)
        },
        total(){
          return this.todos.length
        },
        isAll(){
          return this.doneCount === this.total && this.total != 0
        },
      },
      props:['todos','updataAll','clearAllDone']
    }
</script>

<style>
    /*footer*/
  .todo-footer {
    height: 40px;
    line-height: 40px;
    padding-left: 6px;
    margin-top: 5px;
  }

  .todo-footer label {
    display: inline-block;
    margin-right: 20px;
    cursor: pointer;
  }

  .todo-footer label input {
    position: relative;
    top: -1px;
    vertical-align: middle;
    margin-right: 5px;
  }

  .todo-footer button {
    float: right;
    margin-top: 5px;
  }
</style>