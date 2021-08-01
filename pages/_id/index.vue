<template>
  <v-app>
    <v-container>
      <v-row>
        <v-col cols="4">
          <img :src="game.thumbnail" alt="" />
        </v-col>
        <v-col cols="8">
          <h1>{{ game.title }}</h1>
          <p>{{ game.description }}</p>
          <v-row>
            <v-col v-for="screenshot in game.screenshots" :key="screenshot.id">
              <img :src="screenshot.image" alt="" class="screenshot" />
            </v-col>
          </v-row>
        </v-col>
      </v-row>
    </v-container>
  </v-app>
</template>

<script>
export default {
  async asyncData({ $axios, params }) {
    const config = {
      "x-rapidapi-key": "2a50aee9e6msh55cf8498c0e6c1ap1c932fjsn9403eb2b255d",
      "x-rapidapi-host": "free-to-play-games-database.p.rapidapi.com"
    };
    const result = await $axios.get(
      "https://free-to-play-games-database.p.rapidapi.com/api/game",
      {
        params: { id: params.id },
        headers: config
      }
    );
    return {
      game: result.data
    };
  }
};
</script>

<style lang="scss" scoped>
.screenshot {
  height: 250px;
  width: 100%;
  object-fit: cover;
}
</style>
