<template>
  <v-container>
    <v-row class="text-center">
      <v-col cols="12" class="d-flex align-center justify-center">
        <v-card
          class="card pa-3 d-flex flex-column align-center justify-center"
          width="400"
        >
          <v-text-field
            v-model="textPic"
            outlined
            solo
            flat
            dense
            hide-details
            color="grey"
            height="40"
            placeholder="Ketik nama Anda..."
          ></v-text-field>
          <v-btn
            class="px-3 py-2 my-5"
            color="success"
            :loading="loading"
            @click="handleSubmit"
            >Buat profile picture</v-btn
          >
          <v-img
            class="rounded-circle"
            :style="
              srcImg
                ? 'background: white !important; border: 1px solid grey !important'
                : ''
            "
            :src="srcImg"
            width="150"
            height="150"
          ></v-img>
        </v-card>
      </v-col>
    </v-row>
  </v-container>
</template>

<script>
// import axios from "axios";
export default {
  name: "RandomPic",

  data: () => ({
    textPic: "",
    srcImg: "",
    loading: false,
  }),
  methods: {
    async handleSubmit() {
      this.loading = true;
      this.srcImg = await `https://robohash.org/${this.textPic}`;
      this.loading = false;
    },
  },
};
</script>
<style lang="scss" scoped>
.card {
  background: #a3f7f3 !important;
}
</style>
