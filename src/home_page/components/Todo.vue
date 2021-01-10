<template>
  <div class="todo">
    <h1 class="todo-number">
      There are <span>{{todoNumber}}</span> things left to do
    </h1>

    <ul class="todo-list">
      <li class="todo-list-content" v-for="(item,index) of list" :key="item.id" draggable="true">
        <input type="checkbox" class="finish" @click="handleCheckboxChecked(index)">
        <input v-model="item.content" @keydown.enter="handleInputEnter($event,item.content,index)" @blur="handleInputBlur(item.content,index)">
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
  computed: {
    todoNumber () {
      return this.list.length
    }
  },
  methods: {
    /**
     * 点击checkbox时
     * 发布finishTodoItem事件，
     * 传递当前点击的元素索引
     */
    handleCheckboxChecked (index) {
      this.$emit('finishTodoItem', index)
    },
    /**
     * 修改input中的内容后点击回车时，
     * input失去焦点，
     * 发布changeTodoItem事件，
     * 传递改变后的内容和其索引
     */
    handleInputEnter (event, changeContent, index) {
      event.currentTarget.blur()
      this.$emit('changeTodoItem', changeContent, index)
    },
    /**
     * 修改input中的内容后失去焦点时，
     * 发布changeTodoItem事件，
     * 传递改变后的内容和其索引
     */
    handleInputBlur (changeContent, index) {
      this.$emit('changeTodoItem', changeContent, index)
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
        color #0c8918
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
          display inline-block
          font-size .2rem
          width 80%
          margin-left .1rem
          color #757575
          &:focus
            color #1bd1a5
            font-style italic
</style>
