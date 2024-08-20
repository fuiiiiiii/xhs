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
    // console.log(1111)
    // this.postData()
  },
  onShow() {

    console.log(2222)
    this.postData()
  },
  methods: {
    postData() {

      let json = [{
        props: { "11": "", "22": "", "33": "", "44": "17225588611566642356", "555": "iPhone 15 Pro", "66": "6.6.3", "777": "ios", "888": "15", "2ss": "doust", "16": "", "18": "sss", "19": "2223", "20": "sss", "21": "1.11.0", "22": "393x852", "23": "wifi", "fff9": "carsel", "dss10": "act", "12sss": "@/r", "lll333": "2027", "nnx34": "" }
      }]

      let tmpServerFormat = JSON.stringify({
        records: json,
      });

      let gzData = pako.gzip(tmpServerFormat);

      console.log(Object.prototype.toString.call(gzData.buffer))

      uni.request({
        url: "https://baidu.com",
        method: "POST",
        header: {
          "Content-Encoding": "gzip",
          "Content-Type": "application/json; charset=utf-8",
        },
        data: gzData.buffer,
        success: res => {
          console.log('成功', res)
        },
        fail: err  => {
          console.log('失败', err)
        }
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
