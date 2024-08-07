<template>
  <view class="content">
    <image class="logo" src="/static/logo.png"></image>
    <view class="text-area">
      <text class="title">{{ title }}</text>
    </view>
  </view>
</template>

<script>
import pako from "pako/dist/pako_deflate.min";
export default {
  data() {
    return {
      title: 'Hello',
    }
  },
  onLoad() {
    console.log(1111)
    this.postData()
   },
  methods: {
    postData() {

      let json = [{
        props: { "G1": "", "G2": "", "G3": "", "G4": "17225588611566642356", "G5": "iPhone 15 Pro", "G6": "6.6.3", "G7": "ios", "G8": "15", "G15": "douyinMiniTest", "G16": "", "G18": "SAMA_B243M610", "G19": "91.103.121.72", "G20": "dyMini", "G21": "1.11.0", "G22": "393x852", "G23": "wifi", "G9": "carselection_360_bannervehicleseries", "G10": "act", "G11": "@/pages/car/car", "G17": "2027", "G24": "" }
      }]

      let tmpServerFormat = JSON.stringify({
        records: json,
      });

      let gzData = pako.gzip(tmpServerFormat);

      console.log(Object.prototype.toString.call(gzData.buffer))

      uni.request({
        url: "https://xxxx",
        method: "POST",
        header: {
          "Content-Encoding": "gzip",
          "Content-Type": "application/json; charset=utf-8",
        },
        data: gzData.buffer
      })
    }
  },
}
</script>

<style>
.content {
  display: flex;
  flex-direction: column;
  align-items: center;
  justify-content: center;
}

.logo {
  height: 200rpx;
  width: 200rpx;
  margin-top: 200rpx;
  margin-left: auto;
  margin-right: auto;
  margin-bottom: 50rpx;
}

.text-area {
  display: flex;
  justify-content: center;
}

.title {
  font-size: 36rpx;
  color: #8f8f94;
}
</style>
