<template>
  <v-app>
    <!-- サイドメニュー -->
    <v-navigation-drawer app clipped v-model="drawer" light color="gray">
      <v-card
        class="mx-auto"
        width="256"
        tile>
        <v-list-item>
          <v-list-item-content>
            <v-list-item-title class="text-h6">
              Application
            </v-list-item-title>
            <v-list-item-subtitle>
              subtext
            </v-list-item-subtitle>
          </v-list-item-content>
        </v-list-item>

        <v-list
          dense
          nav
        >
          <v-list-item
            v-for="item in items"
            :key="item.title"
            link
          >
            <v-list-item-icon>
              <v-icon>{{ item.icon }}</v-icon>
            </v-list-item-icon>

            <v-list-item-content>
              <v-list-item-title>{{ item.title }}</v-list-item-title>
            </v-list-item-content>
          </v-list-item>
        </v-list>
      </v-card>
    </v-navigation-drawer>

    <!-- ヘッダー -->
    <!-- <v-app-bar app clippedLeft flat dark color="black darken-3"> -->
    <v-app-bar
      app
      clippedLeft
      flat
      color="black accent-4"
      dense
      dark
    >
      <v-app-bar-nav-icon
        @click.stop="drawer=!drawer"
        >
      </v-app-bar-nav-icon>
      <router-link to="/"> <v-toolbar-title>Page title</v-toolbar-title> </router-link>

      <v-spacer></v-spacer>

      <router-link to="/sub">
        sub
      </router-link>

      <v-btn icon>
      <v-icon>mdi-heart</v-icon>
      </v-btn>

      <v-btn icon>
        <v-icon>mdi-magnify</v-icon>
      </v-btn>

      <v-menu
        left
        bottom
      >
        <template v-slot:activator="{ on, attrs }">
          <v-btn
            icon
            v-bind="attrs"
            v-on="on"
          >
            <v-icon>mdi-dots-vertical</v-icon>
          </v-btn>
        </template>

        <v-list>
          <v-list-item
            v-for="n in 5"
            :key="n"
            @click="() => {}"
          >
            <v-list-item-title>Option {{ n }}</v-list-item-title>
          </v-list-item>
        </v-list>
      </v-menu>
    </v-app-bar>

    <!-- メイン -->
    <v-main>
      <v-container fluid>
      </v-container>
    </v-main>

    <!-- フッター -->
    <v-footer app color="black">
    </v-footer>
  </v-app>
</template>
<style>
.v-application a {
  color: white;
  text-decoration: none;
}
.v-list-item__content {
  align-content: left;
}
#app {
  text-align: left;
}
</style>
<script>
import '@mdi/font/css/materialdesignicons.css'
export default {
  name: 'app',
  data () {
    return {
      drawer: true,
      items: [
        { title: 'Dashboard', icon: 'mdi-view-dashboard' },
        { title: 'Photos', icon: 'mdi-image' },
        { title: 'About', icon: 'mdi-help-box' }
      ],
      right: null
    }
  }
}
</script>
