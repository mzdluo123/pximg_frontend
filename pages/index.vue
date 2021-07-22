<template>
  <v-row justify="center" align="center">
    <v-col cols="12" sm="12" md="12">
      <v-card>
        <v-card-title class="headline">
          欢迎使用RainChan的图库
        </v-card-title>
        <v-card-subtitle>
          所有图片均来自我的pixiv收藏夹,点击图片可以获取链接和图片id,链接可用于你的网站
          <p>刷新页面可以获得一组新的图片</p>
        </v-card-subtitle>

      </v-card>

    </v-col>
    <v-col>
      <ImgPanel v-bind:img-list="imgData"></ImgPanel>
    </v-col>

  </v-row>
</template>
<script>
import ImgPanel from "../components/ImgPanel";

export default {
  components: {ImgPanel},
  head() {
    return {
      title: "主页"
    }
  },
  data() {
    return {
      imgData: []
    }
  },
  async asyncData({params, $axios}) {
    const  rsp =await $axios.get(`/list?random_img=true`)
    return {imgData: rsp.data}
  }
}
</script>
