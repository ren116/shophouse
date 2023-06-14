<template>
  <v-layout class="overflow" style="height: 56px">
    <v-container class="d-flex w-100" v-model="value" color="teal" grow>
      <v-btn>
        <v-icon>mdi-history</v-icon>

        Recents
      </v-btn>

      <v-btn>
        <v-icon>mdi-heart</v-icon>

        Favorites
      </v-btn>

      <v-btn>
        <v-icon>mdi-map-marker</v-icon>

        Nearby
      </v-btn>
    </v-container>
  </v-layout>
</template>

<script>
export default {
  data: () => ({ value: 1 }),
};
</script>
