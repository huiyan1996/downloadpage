<template>
  <div class="container">
    <div class="row">
      <div class="col-12 px-0">
        <img src="@/assets/img/banner.jpg" width="100%" alt="" srcset="">
      </div>
      <div class="bottomBg">
        <div class="text-center">
          <button type="button" class="btn btn-primary">点击下载安装 {{systemType}}</button>
        </div>
        <div class="mt-4">
          <b-badge pill variant="primary">温馨提示</b-badge>
          <p class="mt-3">下载完成打开应用，IOS系统会提示“未受信任的企业级开发者”。</p>
          <p class="mt-3">解决方法如下:</p>
          <ol>
            <li>点击手机中的设置-点击通用，进入通用设置。</li>
            <li>寻找通用设置中的设备管理，进入通用设置，查询刚刚提示未受信任的企业级开发者前缀，点击进入。</li>
            <li>在弹出窗口点击信任操作，即完成信任应用</li>
          </ol>
          <p class="text-center mt-5">(返回桌面即可打开应用了)</p>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
// @ is an alias to /src
import HelloWorld from '@/components/HelloWorld.vue'

export default {
  name: 'Home',
  components: {
    HelloWorld
  },
  data: function() {
    return {
      systemType: null
    }
  },
  mounted: function() {
    this.systemType = this.getMobileOperatingSystem()
  },
  methods: {
    getMobileOperatingSystem() {
      var userAgent = navigator.userAgent || navigator.vendor || window.opera;

      // Windows Phone must come first because its UA also contains "Android"
      if (/windows phone/i.test(userAgent)) {
          return "Windows Phone";
      }

      if (/android/i.test(userAgent)) {
          return "Android";
      }

      // iOS detection from: http://stackoverflow.com/a/9039885/177710
      if (/iPad|iPhone|iPod/.test(userAgent) && !window.MSStream) {
          return "iOS";
      }

      return null;
    }
  }
}
</script>
