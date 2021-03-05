<template>
  <v-container>
    <v-row>
      <v-col>
        <div>
          <v-text-field
            v-model="query"
            label="Search"
            class="searchField"
            placeholder="Placeholder"
            dense
          >
          </v-text-field>
          <v-btn @click="handleSearchManga"
            ><v-icon left> mdi-magnify </v-icon>Search</v-btn
          >
        </div>
        <v-card
          v-for="manga in results"
          :key="manga.mal_id"
          class="ma-2 mangaCard"
          cols="12"
          md="4"
          outlined
          @click="handleMangaClick(manga)"
        >
          <v-list-item three-line
            ><img :src="manga.image_url" alt="" class="cardImg" />
            <v-list-item-content>
              <!-- <div class="overline mb-4">
                Publishing: {{ manga.publishing }}
              </div> -->
              <v-list-item-title class="headline mb-1">
                {{ manga.title }}</v-list-item-title
              >
              <v-list-item-subtitle>
                {{ manga.synopsis }}
              </v-list-item-subtitle>
            </v-list-item-content>
          </v-list-item>
        </v-card>
      </v-col></v-row
    ></v-container
  >
</template>

<script>
import axios from 'axios'
export default {
  data() {
    return {
      query: '',
      results: [],
    }
  },
  methods: {
    handleSearchManga() {
      const url = `https://api.jikan.moe/v3/search/manga?q=${this.query}&page=1`
      axios.get(url).then((res) => {
        console.log(res.data)
        this.results = res.data.results
      })
    },
    handleMangaClick(manga) {
      console.log('MANGA', manga)
      window.location = manga.url
    },
  },
}
</script>

<style lang="css" scoped>
.mangaCard {
  width: 450px;
  margin: 2rem;
}
.searchField {
  width: 450px;
}
.cardImg {
  margin: 5px;
  margin-right: 10px;
  width: 80px;
}
</style>
