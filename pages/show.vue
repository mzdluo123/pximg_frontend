<template>

  <div class="fill-height">
    <v-row class="ma-1">
      <v-col cols="9" lg="9" md="9" sm="12">
        <v-img
          v-bind:src="`${$axios.defaults.baseURL}/img?img_id=${$route.query.id}`"
          v-bind:lazy-src="`${$axios.defaults.baseURL}/img?img_id=${$route.query.id}&web=true`"

        >
          <template v-slot:placeholder>
            <v-row
              class="fill-height ma-0"
              align="center"
              justify="center"
            >
              <v-progress-circular
                indeterminate
                color="grey lighten-5"
              ></v-progress-circular>
            </v-row>
          </template>
        </v-img>
      </v-col>

      <v-col  class="mr-3 mt-3">
        <v-card v-show="show"  class="fill-height">
          <v-card-title>{{ imgInfo.title}}</v-card-title>
          <v-card-subtitle>{{imgInfo.id}}</v-card-subtitle>
          <v-card-text>
            <CopyText></CopyText>
          </v-card-text>

        </v-card>

      </v-col>
    </v-row>

  </div>

</template>

<script>

import CopyText from "../components/CopyText";
export default {
  name: "show",
  components: {CopyText},
  layout: "empty",
  head() {
    return {
      title: "图片显示"
    }
  },
  data() {
    return {
      show: false,
      imgInfo: {
        title: "",
        id:1
      }
    }
  },
  async asyncData({params, route, $axios}) {

    const info = await $axios.get("/imginfo", {params: {img_id: route.query.id}})
    console.log(info.data)
    return {imgInfo: info.data, show: true}
  }
}
</script>

<style scoped>

</style>
