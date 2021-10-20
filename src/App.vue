<template>
  <v-app :dark="isDark">
    <v-card color="grey lighten-4" flat tile>
      <v-toolbar dense color="primary" dark>
        <v-app-bar-nav-icon></v-app-bar-nav-icon>
        <v-toolbar-title class="headline">Список дел</v-toolbar-title>

        <v-spacer></v-spacer>

        <v-tooltip bottom>
          <template v-slot:activator="{ on }">
            <v-btn icon @click="show = !show" v-on="on">
              <v-icon @click="isDark = !isDark">
                {{ show ? 'mdi-check-circle-outline' : 'mdi-check-circle' }}
              </v-icon>
            </v-btn>
          </template>
          <span>{{ isDark ? 'Темная тема' : 'Светлая тема'}}</span>
        </v-tooltip>

      </v-toolbar>

      <appBoard></appBoard>
    </v-card>
  </v-app>
</template>

<script>
import Board from "@/components/Board";

export default {
  components: {
    appBoard: Board
  },
  data: () => ({
    show: true,
    isDark: true
  }),
};
</script>
