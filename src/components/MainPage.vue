<template>
  <v-container>
    <v-row class="text-center">
      <v-col class="mb-4">
        <h1 class="display-2 font-weight-bold mb-3">
          Cryptocurrency price tracker
        </h1>

        <p class="subheading font-weight-regular">
          This tracker was made to showcase Vue's prototyping abilities. From Wuzado, with love. ❤️
        </p>
      </v-col>
    </v-row>
    <v-row class="trackers">
      <v-col class="mb-4">
        <div v-for="cryptocurr in cryptos" :key=cryptocurr.id>
          <CryptoCard :cryptocurr=cryptocurr />
        </div>
      </v-col>
    </v-row>
  </v-container>
</template>

<script>
import CryptoCard from "@/components/CryptoCard"
export default {
  name: "MainPage",
  components: {
    CryptoCard
  },
  data: () => ({
    cryptos: [
      {
        name: "bitcoin"
      },
      {
        name: "litecoin"
      },
      {
        name: "dogecoin"
      }
    ]
  })
}
</script>
