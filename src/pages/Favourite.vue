<template>
  <v-ons-page>
    <custom-toolbar v-bind="toolbarInfo"></custom-toolbar>
    <v-ons-list>
      <v-ons-list-item v-for="favourite in favourites" :key="favourite"
        modifier="chevron"
        @click="transition(favourite)"
      >
        {{ favourite }}
      </v-ons-list-item>
    </v-ons-list>
  </v-ons-page>
</template>

<script>
const transitionPage = {
  template: `
    <v-ons-page>
      <custom-toolbar backLabel="Back">
        {{ favourite }}
      </custom-toolbar>
      <p style="text-align: center">
        Use the VOnsBackButton
      </p>
    </v-ons-page>
    `
};

export default {
  data() {
    return {
      favourites: ['none', 'default', 'slide-ios', 'slide-md', 'lift-ios', 'lift-md', 'fade-ios', 'fade-md']
    };
  },
  methods: {
    transition(name) {
      this.$store.commit('navigator/options', {
        // Sets favourites
        favourite: name,
        // Resets default options
        callback: () => this.$store.commit('navigator/options', {})
      });

      this.$store.commit('navigator/push', {
        extends: transitionPage,
        data() {
          return {
            favourite: name
          }
        }
      });
    }
  }
};
</script>
