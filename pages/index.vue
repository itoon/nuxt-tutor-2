<template>
  <v-app>
    <v-container>
      <v-row>
        <v-col cols="8">
          <v-row>
            <v-col cols="12" v-for="item in gameList" :key="`game-${item.id}`">
              <base-game-card
                :title="item.title"
                :id="item.id"
                :thumbnail="item.thumbnail"
                :short_description="item.short_description"
                :genre="item.genre"
                :platform="item.platform"
              ></base-game-card>
              <base-game-card v-bind="item"></base-game-card>
            </v-col>
          </v-row>
        </v-col>
        <v-col cols="4">
          <v-row>
            <v-col cols="12" v-for="item in gameList" :key="`game2-${item.id}`">
              <img :src="item.thumbnail" alt="" />
            </v-col>
          </v-row>
        </v-col>
      </v-row>
    </v-container>
  </v-app>
</template>

<script>
export default {
  /*
  async asyncData(context) {
    context.$axios.get....
  }
  */
  async asyncData({ $axios }) {
    const config = {
      "x-rapidapi-key": "2a50aee9e6msh55cf8498c0e6c1ap1c932fjsn9403eb2b255d",
      "x-rapidapi-host": "free-to-play-games-database.p.rapidapi.com"
    };
    const result = await $axios.get(
      "https://free-to-play-games-database.p.rapidapi.com/api/games",
      {
        headers: config
      }
    );
    return {
      gameList: result.data
    };
  },
  async mounted() {
    // const config = {
    //   "x-rapidapi-key": "2a50aee9e6msh55cf8498c0e6c1ap1c932fjsn9403eb2b255d",
    //   "x-rapidapi-host": "free-to-play-games-database.p.rapidapi.com"
    // };
    // const result = await this.$axios.get(
    //   "https://free-to-play-games-database.p.rapidapi.com/api/games",
    //   {
    //     headers: config
    //   }
    // );
    // this.gameList = result.data;
  },
  methods: {},
  data() {
    return {
      gameList: []
    };
  }
};
</script>

<style lang="scss" scoped>
@media (min-width: 1904px) {
  .container {
    max-width: 1185px;
  }
}
</style>
