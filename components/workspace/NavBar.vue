<template>
  <v-app-bar app color="primary" dark clipped-right clipped-left dense>
    <v-toolbar-title>{{ user.name }}</v-toolbar-title>

    <v-divider class="mx-4" inset vertical></v-divider>
    <span class="subheading">{{ user.email }}</span>
    <v-spacer></v-spacer>
    <v-btn text @click="logout">
      Logout
    </v-btn>

    <template v-slot:extension>
      <v-tabs align-with-title>
        <v-tabs-slider color="yellow"></v-tabs-slider>

        <v-tab nuxt to="/workspace/er">Entity-Relation</v-tab>
        <v-tab nuxt to="/workspace/relational">Relational</v-tab>
      </v-tabs>
    </template>
  </v-app-bar>
</template>

<script>
import { mapGetters } from 'vuex'
export default {
  computed: {
    ...mapGetters({
      loggedIn: 'calls/loggedIn',
      user: 'calls/userInfo'
    })
  },
  methods: {
    logout() {
      this.$store.dispatch('calls/logout')
    }
  }
}
</script>
