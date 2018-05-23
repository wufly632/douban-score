<template>
  <div class="index">
    <div class="header">
      <input type="text" placeholder="搜索" class="index-search">
    </div>
  </div>
</template>

<script>
import card from '@/components/card'

export default {
  data () {
    return {
      motto: 'Hello World',
      userInfo: {}
    }
  },

  components: {
    card
  },

  methods: {
    bindViewTap () {
      const url = '../logs/main'
      wx.navigateTo({ url })
    },
    getUserInfo () {
      // 调用登录接口
      wx.login({
        success: () => {
          wx.getUserInfo({
            success: (res) => {
              this.userInfo = res.userInfo
            }
          })
        }
      })
    },
    clickHandle (msg, ev) {
      console.log('clickHandle:', msg, ev)
    }
  },

  created () {
    // 调用应用实例的方法获取全局数据
    this.getUserInfo()
  }
}
</script>

<style scoped>
.header{background-color: #0FC75E; padding: 20rpx 0}
.index-search{
  width: 90%;
  height: 20rpx;
  margin: 0 5%;
  background-color: #FFF;
  border-radius: 10rpx;
}
.index-search::input-placeholder { text-align: center }
</style>
