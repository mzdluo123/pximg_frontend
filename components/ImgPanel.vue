<template>

    <v-card
      class="d-flex align-content-start flex-wrap"
      flat
    >
      <v-card
        v-for="item in imgList"
        :key="item.url"
        class="ma-2"
        @click="click_card(item.id)"
      >
      <v-img
        v-bind:src="`${$axios.defaults.baseURL}/img?img_id=${item.id}&web=true`"
        cover
        width="auto"
        max-width="260"
        height="320"
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

    </v-card>
    </v-card>

</template>

<script>

export default {
  name: "ImgPanel",
  props: ["imgList"],
  methods: {
    click_card: function (id) {

      this.$router.push({path:'show',query:{id:id}})
    }
  }
}
</script>

<style scoped>

</style>
