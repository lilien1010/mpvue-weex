<template>
  <div class="pages--test1">
    <zk-head backText="首页" :title="pageInfo.title" v-if="asyncFlag"></zk-head>
    <x-cell title="会员" value="dd" url="http://www.baidu.com"></x-cell>
    <zk-foot></zk-foot>
  </div>
</template>

<script>
  import { THEME_GETPAGE_GET } from '@/service/api/apiUrl'
  export default {
    config: {
      'navigationBarTitleText': '测试一'
    },
    data () {
      return {
        pageInfo: '',
        asyncFlag: false
      }
    },
    mounted () {
      this.init()
    },
    methods: {
      async init () {
        this.$loading = true
        this.pageInfo = await this.$api.get(THEME_GETPAGE_GET, 'clientType=' + this.$client + '&url=' + this.$route.path)
        this.$loading = false
        this.asyncFlag = true
        // console.info('测试一页面', this.pageInfo)
      }
    }
  }
</script>

<style scoped lang="less">
  .pages--test1 {
    width: 100%;
  }
</style>

