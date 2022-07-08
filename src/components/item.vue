<template>
  <li
    @mouseenter="isEnter = true"
    @mouseleave="isEnter = false"
    :class="isEnter ? 'enter' : ''"
  >
    <label>
      <input
        type="checkbox"
        :checked="todosObj.done"
        @change="updateT(todosObj.id, $event)"
      />
      <span>{{ todosObj.title }}</span>
    </label>
    <button
      class="btn btn-danger"
      @click="delT(todosObj.id)"
      :style="{ display: isEnter ? 'block' : 'none' }"
    >
      删除
    </button>
  </li>
</template>

<script>
export default {
  name: "Item",
  data() {
    return {
      isEnter: false,
      chen: "",
    };
  },
  methods: {
    // 删除
    delT(id) {
      if (confirm("确定删除么?")) {
        this.delTodo(id);
      }
    },
    // 响应勾选 or 取消勾选
    updateT(id, event) {
      this.updateTodo(id, event.target.checked);
    },
  },
  props: {
    todosObj: Object,
    delTodo: Function,
    updateTodo: Function,
  },
};
</script>

<style>
/*item*/
li {
  list-style: none;
  height: 36px;
  line-height: 36px;
  padding: 0 5px;
  border-bottom: 1px solid #ddd;
}

li label {
  float: left;
  cursor: pointer;
}

li label li input {
  vertical-align: middle;
  margin-right: 6px;
  position: relative;
  top: -1px;
}

li button {
  float: right;
  display: none;
  margin-top: 3px;
}

li:before {
  content: initial;
}

li:last-child {
  border-bottom: none;
}

.enter {
  background-color: #ddd;
}
</style>