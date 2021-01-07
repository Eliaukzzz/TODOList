<template>
  <div class="done">
    <h1 class="done-number">
      There are <span>{{doneNumber}}</span> things have been done
    </h1>
    <ul class="done-list">
      <li class="done-list-content" v-for="(item,index) of list" :key="item.id">
        <p @click="handleDoneDelete(index)">{{item.content}}</p>
      </li>
    </ul>
  </div>
</template>

<script>
export default {
  name: 'HomeDone',
  props: {
    list: Array
  },
  computed: {
    doneNumber () {
      return this.list.length
    }
  },
  methods: {
    handleDoneDelete (index) {
      this.$emit('deleteDoneItem', index)
    }
  }
}
</script>

<style lang="stylus" scoped>
  .done
    min-height 1.4rem
    background-color #fff
    color #0DBC79
    padding 0 .1rem
    .done-number
      border-bottom .01rem solid #ccc
      font-size .15rem
      margin-bottom .02rem
      margin-right 1.5rem
      span
        font-size .22rem
        color #0DAA00
    .done-list
      font-size .2rem
      .done-list-content
        height .3rem
        padding-left .02rem
        margin 0 0 .02rem
        border-bottom .01rem solid #ccc
        p
          display inline-block
          line-height 100%
          margin-left .1rem
          color #757575
          text-decoration line-through
</style>
