<template>
  <div class="todo">
    <h1 class="todo-number">
      There are <span>{{todoNumber}}</span> things left to do
    </h1>

    <ul class="todo-list">
      <li class="todo-list-content" v-for="(item,index) of todoList" :key="item.id">
        <input type="checkbox" class="finish" @click="handleCheckboxChecked(index)">
        <input v-if="show" v-model="item.content">
        <p @click="handleTodoClick(item.content, index)">{{item.content}}</p>
      </li>
    </ul>
  </div>
</template>

<script>
export default {
  name: 'HomeTodo',
  props: {
    list: Array
  },
  data () {
    return {
      todoList: this.list,
      show: false
    }
  },
  computed: {
    todoNumber () {
      return this.list.length
    }
  },
  methods: {
    handleCheckboxChecked (index) {
      this.$emit('finishTodoItem', index)
    },
    handleTodoClick (changedTodo, index) {
      // 待实现
    }
  }
}
</script>

<style lang="stylus" scoped>
  .todo
    background-color #fff
    color #0DBC79
    padding 0 .1rem
    min-height 1.3rem
    .todo-number
      border-bottom .01rem solid #ccc
      font-size .15rem
      margin-bottom .02rem
      margin-right 2rem
      span
        font-size .22rem
        color #0DAA00
    .todo-list
      font-size .2rem
      .todo-list-content
        position relative
        height .3rem
        padding-left .02rem
        margin 0 0 .02rem
        border-bottom .01rem solid #ccc
        .finish
          float left
          margin .06rem 0
          height .18rem
          width .18rem
        input
          position absolute
          top -.01rem
          width 80%
          height 100%
          color #ccc
          font-size .2rem
          line-height 100%
          margin-left .2rem
        p
          display inline-block
          width 80%
          line-height 100%
          margin-left .2rem
          color #757575
</style>
