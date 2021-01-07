<template>
  <div>
    <home-header @addNewTodo="addNewTodo"></home-header>
    <home-todo :list="todoList" @finishTodoItem="finishTodoItem"></home-todo>
    <home-done :list="doneList" @deleteDoneItem="deleteDoneItem"></home-done>
  </div>
</template>

<script>
import HomeHeader from './components/Header'
import HomeTodo from './components/Todo'
import HomeDone from './components/Done'

export default {
  name: 'Home',
  components: {
    HomeHeader,
    HomeTodo,
    HomeDone
  },
  data () {
    return {
      todoList: [{
        id: '1',
        content: '起床写代码'
      }],
      doneList: []
    }
  },
  methods: {
    addNewTodo (item) {
      let newTodo = {
        id: (this.todoList.length + 1).toString(),
        content: item
      }
      this.todoList.push(newTodo)
    },
    finishTodoItem (index) {
      this.doneList.push(this.todoList[index])
      this.todoList.splice(index, 1)
    },
    deleteDoneItem (index) {
      this.doneList.splice(index, 1)
    }
  }
}
</script>

<style lang="stylus" scoped>
  div
    background-color: #fff;
    border-radius .05rem
</style>
