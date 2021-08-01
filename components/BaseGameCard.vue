<template>
  <v-row>
    <v-col cols="3">
      <img :src="thumbnail" alt="" class="thumbnail" />
    </v-col>
    <v-col cols="7">
      <nuxt-link :to="`/${id}`">
        <h1>{{ title }}</h1>
      </nuxt-link>
      <p>{{ short_description }}</p>
      <div class="genre">{{ genre }}</div>
    </v-col>
    <v-col cols="2" align-self="center">
      <div class="d-flex">
        <svg
          v-if="isPlatformWindows(platform)"
          aria-hidden="true"
          focusable="false"
          data-prefix="fab"
          data-icon="windows"
          role="img"
          xmlns="http://www.w3.org/2000/svg"
          viewBox="0 0 448 512"
          class="svg-inline--fa fa-windows fa-w-14 fa-3x svg"
        >
          <path
            fill="currentColor"
            d="M0 93.7l183.6-25.3v177.4H0V93.7zm0 324.6l183.6 25.3V268.4H0v149.9zm203.8 28L448 480V268.4H203.8v177.9zm0-380.6v180.1H448V32L203.8 65.7z"
            class=""
          ></path>
        </svg>
        <div>FREE</div>
      </div>
    </v-col>
  </v-row>
</template>

<script>
export default {
  // props: ["item"],
  // props: {
  //   item: {
  //     type: Object
  //   }
  // },
  props: {
    thumbnail: {
      type: String
    },
    title: {
      type: String
    },
    id: {
      type: String
    },
    short_description: {
      type: String
    },
    genre: {
      type: String
    },
    platform: {
      type: String
    }
  },
  methods: {
    isPlatformWindows(platform) {
      if (platform.includes("Windows")) {
        return true;
      } else {
        return false;
      }
    }
  }
};
</script>

<style lang="scss" scoped>
.thumbnail {
  max-width: 100%;
}
.svg {
  max-width: 20px;
}
</style>
