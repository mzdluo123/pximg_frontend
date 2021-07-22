<template>
  <v-row justify="center" align="center">
    <v-col cols="12" sm="12" md="12">
      <v-card>
        <v-card-title class="headline">
          基本配置
        </v-card-title>
        <v-card-subtitle>
          请在这里配置你需要的参数
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
