<template>
  <div class="about">
    <div class="text">about me {{userInfo.userName}}</div>
    <div>
      <el-button type="default" @click="getGithubUserInfo">测试axios</el-button>
    </div>
    <div>测试结果：{{result}}</div>
  </div>
</template>

<script>
import { mapState } from 'vuex'
export default {
  name: 'about',
  data () {
    return {
      result: null
    }
  },
  computed: {
    ...mapState({
      // 登陆者信息
      userInfo: state => state.userInfo.userInfo
    })
  },
  methods: {
    async getGithubUserInfo () {
      this.result = await this.$axios('/business/common/get_host')
    }
  }
}
</script>

<style lang="less">
.about {
  text-align: center;
  .text {
    color: pink;
    text-align: center;
  }
}
</style>
