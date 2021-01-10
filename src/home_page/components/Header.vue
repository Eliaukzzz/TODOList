<template>
  <div class="header">
    <h1 class="header-title">TODOLIST</h1>
    <input class="header-input" placeholder="Add New ToDo" @keydown.enter="handleEnterDown" v-model="newContent">
  </div>
</template>

<script>
export default {
  name: 'HomeHeader',
  data () {
    return {
      newContent: ''
    }
  },
  methods: {
    /**
     * 输入新日程后按下回车时
     * 如果新日程为空，不做处理
     * 如果新日程不为空，添加新日程
     */
    handleEnterDown () {
      if (this.newContent === '') {
        return
      }
      this.$emit('addNewTodo', this.newContent)
      this.newContent = ''
    }
  }
}
</script>

<style lang="stylus" scoped>
  .header
    height .5rem
    background-color #0DBC79
    border-radius .05rem .05rem 0 0
    .header-title
      float left
      color #fff
      margin-left .1rem
      line-height .5rem
      font-size .3rem
      font-weight bold
    .header-input
      float right
      height .3rem
      width 1.5rem
      margin .1rem .1rem
      padding-left 2%
      padding-right 2%
      line-height .3rem
      font-size .22rem
      border-radius .05rem
</style>
