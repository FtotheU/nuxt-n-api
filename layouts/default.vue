<template>
  <v-app dark>
    <v-card elevation="12" width="256" class="ma-3">
      <v-navigation-drawer floating permanent app class="accent">
        <v-app-bar class="primary" dense>
          <v-toolbar-title v-text="title" />
        </v-app-bar>
        <v-list dense rounded disabled>
          <v-list-item-group v-model="selectItem" mandatory color="yellow">
            <v-subheader>MENU</v-subheader>
            <v-list-item v-for="list in lists" :key="list.title" link>
              <v-list-item-icon>
                <v-icon>{{ list.icon }}</v-icon>
              </v-list-item-icon>

              <v-list-item-content>
                <v-list-item-title>{{ list.title }}</v-list-item-title>
              </v-list-item-content>
            </v-list-item>
          </v-list-item-group>
        </v-list>
        <!-- <p class="primary">555</p>
        <p class="secondary">555</p>
        <p class="accent">555</p>
        <p class="info">555</p>
        <p class="warning">555</p>
        <p class="error">555</p>
        <p class="success">555</p> -->
        <template v-slot:append>
          <v-list-item two-line>
            <v-list-item-avatar>
              <img src="https://randomuser.me/api/portraits/women/81.jpg" />
            </v-list-item-avatar>

            <v-list-item-content>
              <v-list-item-title>Jane Smith</v-list-item-title>
              <v-list-item-subtitle>Logged In</v-list-item-subtitle>
            </v-list-item-content>
          </v-list-item>
          <div class="ma-2">
            <v-btn block> Logout </v-btn>
          </div>
        </template>
      </v-navigation-drawer>
    </v-card>
    <v-app-bar fixed app dense class="primary"> </v-app-bar>
    <v-main>
      <v-container>
        <nuxt />
      </v-container>
    </v-main>

    <!-- <v-footer absolute app
      ><v-col class="text-center" cols="12">
        <span
          >&copy; {{ new Date().getFullYear() }} - Thank you for using
          Spotifu.</span
        >
      </v-col>
    </v-footer> -->
  </v-app>
</template>

<script>
import index from '~/pages/index.vue'

export default {
  pages: {
    index,
  },
  data() {
    return {
      lists: [
        { title: 'Home', icon: 'mdi-home' },
        { title: 'Artists', icon: 'mdi-account' },
        { title: 'Albums', icon: 'mdi-folder' },
        { title: 'Title', icon: 'mdi-book' },
        { title: 'My favorites', icon: 'mdi-bookmark' },
        { title: 'Search', icon: 'mdi-magnify' },
      ],
      title: 'Cartoon',
      selectedItem: 1,
    }
  },
}
</script>

<style></style>
