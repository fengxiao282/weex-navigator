<template>
  <div class="wrapper" @click="update">
    <image :src="logoUrl" class="logo"></image>
    <text class="title">click me to new page</text>
  </div>
</template>

<style>
  .wrapper { align-items: center; margin-top: 120px; }
  .title { padding-top:40px; padding-bottom: 40px; font-size: 48px; }
  .logo { width: 360px; height: 156px; }
  .desc { padding-top: 20px; color:#888; font-size: 24px;}
</style>

<script>
  var navigator = weex.requireModule('navigator')
  var modal = weex.requireModule('modal')

  export default {
    mounted: function () {
      console.log('url:', weex.config.bundleUrl)
    },
    data () {
      return {
        logoUrl: 'http://img1.vued.vanthink.cn/vued08aa73a9ab65dcbd360ec54659ada97c.png',
        target: 'World'
      }
    },
    methods: {
      update: function (event) {
        navigator.push({
          url: 'http://192.168.3.85:8088/weex/new.js',
          animated: "true"
        }, event => {
          modal.toast({ message: 'callback: ' + event })
        })
      }
    }
  }
</script>
