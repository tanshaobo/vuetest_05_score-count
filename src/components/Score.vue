<template>
  <div class="score">
    <h1>
      初中一年级学生考试分数统计
    </h1>
    <div class="control">
      <label for="studentName">
        学生：
      </label>
      <input type="text" v-model="newTest.studentName" id="studentName"/>
       <label for="score">
        分数：
      </label>
      <input type="text" v-model="newTest.score" id="score"/>
      <button @click="addTestScore">添加</button>
    </div>
    <ul>
      <li v-for="test in tests" v-bind:key="test.index">
        {{test.studentName}}:{{test.score}}
      </li>
    </ul>
    <div class="total">
      <span>总分：{{total}}</span>
      <span>平均分：{{average}}</span>
    </div>
  </div>
</template>

<script>
export default {
  name: 'Score',
  data () {
    return {
      newTest: {
        studentName: '傻根',
        score: 0
      },
      tests: [
        {
          studentName: '世界',
          score: 76
        },
        {
          studentName: '诚哥',
          score: 84
        },
        {
          studentName: '言叶',
          score: 95
        }
      ],
      total: 0,
      average: 0
    }
  },
  created () {
    let that = this
    that.totalScore()
    that.averageScore()
  },
  methods: {
    addTestScore () {
      let that = this
      that.tests.push({
        studentName: that.newTest.studentName,
        score: that.newTest.score
      })
      that.totalScore()
      that.averageScore()
      that.newTest.studentName = '傻根'
      that.newTest.score = 0
    },
    totalScore () {
      let total = 0
      let that = this
      for (let i = 0; i < that.tests.length; i++) {
        total += parseInt(that.tests[i].score)
      }
      that.total = total
    },
    averageScore () {
      let average
      let that = this
      average = parseInt(that.total / that.tests.length)
      that.average = average
    }
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped lang="stylus">
.score
  width 800px
  margin auto
h1
  display inline-block
  margin 0 0 25px
  border-bottom 2px solid #69f
  padding-bottom 5px
  color #69f
  text-shadow 1px 1px 0 rgba(0,0,0,.4)
.control
  margin-bottom inline-block
  label,
  span
    display inline-block
    vertical-align middle
  input
    padding 5px 10px
    box-sizing border-box
    border-radius 3px
    border 1px solid rgba(0,0,0,.5)
    box-shadow 0 0 4px 0 rgba(0,0,0,.15)
    &:focus,
    &:active
      outline none
      box-shadow 0 0 4px 0 rgba(0,169,244,.9)
      border-color rgba(0,169,244,1)
  button
    padding 0 20px
    background #ff0030
    color #FFF
    font-size 16px
    border 1px dashed #FFF
    border-radius 3px
    box-shadow 0 0 0 4px #ff0030, 2px 1px 6px 4px rgba(10,10,0,.5)
    text-shadow -1px -1px #aa3030
    box-sizing border-box
    margin-left 10px
    cursor pointer
    vertical-align sub
    outline none
ul
  list-style none outside none
  text-align left
  margin 0 0 20px
  padding 0 0 20px
  display flex
  flex-wrap wrap
  border-bottom 3px double rgba(0,0,0,.8)
  li
    line-height 30px
    flex 0 0 33.3333%
.total
  display flex
  justify-content space-around
  font-size 24px
  font-weight bold
</style>
