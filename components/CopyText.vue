<template>
  <div>
    <v-card
      flat
      class="">

      <v-card-title>{{title}}</v-card-title>
      <v-card-text class="">
        <p>{{text}}</p>
        <v-btn color="primary" @click="onclickBtn">点击复制</v-btn>
      </v-card-text>
    </v-card>
  </div>
</template>

<script>
export default {
  name: "CopyText",
  props: ["title", "text"],
  methods: {
    onclickBtn: function () {
      const aux = document.createElement("input");
      aux.setAttribute("value", this.text);
      document.body.appendChild(aux);
      aux.select();
      document.execCommand("copy");
      document.body.removeChild(aux);

    }
  }
}
</script>

<style scoped>

</style>
