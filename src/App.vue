<template>
  <div class="todo-container">
    <div class="todo-wrap">
      <Header :addTodo="addTodo"></Header>
      <List 
        v-show="todos.length" 
        :todos="todos" 
        :delTodo="delTodo" 
        :updateTodo="updateTodo"
      ></List>
      <Footer 
        v-show="todos.length" 
        :todos="todos" 
        :updataAll="updataAll" 
        :clearAllDone="clearAllDone"
      ></Footer>
    </div>
  </div>
</template>

<script>
    import Header from './components/Header'
    import Footer from './components/Footer'
    import List from './components/List'
    export default {
        name:'App',
        components:{
            Header,
            Footer,
            List
        },
        data() {
          return {
            todos:[
              {id:'001',title:'吃饭',done:true},
              {id:'002',title:'睡觉',done:false},
              {id:'003',title:'上课',done:true},
            ]
          }
        },
        methods: {
          // 添加一个todo
          addTodo(todoObj){
            this.todos.unshift(todoObj)
          },
          // 删除一个todo
          delTodo(id){
            this.todos = this.todos.filter((t)=>{
                return t.id !== id
            })
          },
          // 更新一个todo
          updateTodo(id,done){
            this.todos.forEach((todosObj)=>{
                if (todosObj.id === id)  todosObj.done = done
            })
          },
          // 更新所有
          updataAll(done){
            this.todos.forEach((t)=>{
              t.done = done
            })
          },
          // 清除所有已完成
          clearAllDone(){
            this.todos = this.todos.filter((t)=>{
                return !t.done
            })
          }
        },
    }
</script>

<style>
/*base*/
body {
  background: #fff;
}

.btn {
  display: inline-block;
  padding: 4px 12px;
  margin-bottom: 0;
  font-size: 14px;
  line-height: 20px;
  text-align: center;
  vertical-align: middle;
  cursor: pointer;
  box-shadow: inset 0 1px 0 rgba(255, 255, 255, 0.2), 0 1px 2px rgba(0, 0, 0, 0.05);
  border-radius: 4px;
}

.btn-danger {
  color: #fff;
  background-color: #da4f49;
  border: 1px solid #bd362f;
}

.btn-danger:hover {
  color: #fff;
  background-color: #bd362f;
}

.btn:focus {
  outline: none;
}

.todo-container {
  width: 600px;
  margin: 0 auto;
}
.todo-container .todo-wrap {
  padding: 10px;
  border: 1px solid #ddd;
  border-radius: 5px;
}
</style>