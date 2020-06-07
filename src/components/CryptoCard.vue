<template>
  <v-card class="mx-auto" max-width="344">
    <v-card-title>{{info.name}} ({{info.symbol}})</v-card-title>

    <v-card-subtitle>{{info.market_data.current_price.usd}} USD</v-card-subtitle>

    <v-card-actions @click="show = !show">
      <v-btn>Description</v-btn>
      <v-spacer></v-spacer>

      <v-btn icon>
        <v-icon>{{ show ? "mdi-chevron-up" : "mdi-chevron-down" }}</v-icon>
      </v-btn>
    </v-card-actions>

    <v-expand-transition>
      <div v-show="show">
        <v-divider></v-divider>
        <v-card-text>{{info.description.en}}</v-card-text>
      </div>
    </v-expand-transition>
  </v-card>
</template>


<script>
export default {
  name: "CryptoCard",
  props: {
    cryptocurr: String,
  },
  data: () => ({
    show: false,
    info: null
  }),
  mounted() {
    this.$http
      .get("https://api.coingecko.com/api/v3/coins/" + this.cryptocurr.name)
      .then(response => {this.info = response.data});
  }
};
</script>