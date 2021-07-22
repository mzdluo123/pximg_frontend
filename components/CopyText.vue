<template>
  <div>
    <v-card
      flat
      class="grey white--text">

      <v-card-title>代码</v-card-title>
      <v-card-text class="white--text">
        <p> 这里是文字</p>
        <v-btn color="primary" @click="onclickBtn">点击复制</v-btn>
      </v-card-text>
    </v-card>
  </div>
</template>

<script>
export default {
  name: "CopyText",
  props:["title","text"],
  methods:{
    onclickBtn:function () {

    }
  }
}
</script>

<style scoped>

</style>
