<template>
  <v-ons-page>
    <custom-toolbar v-bind="toolbarInfo"></custom-toolbar>
    <v-ons-list>
      <v-ons-list-item v-for="folder in folders" :key="folder"
        modifier="chevron"
        @click="transition(folder)"
      >
        {{ folder }}
      </v-ons-list-item>
    </v-ons-list>
  </v-ons-page>
</template>

<script>
const transitionPage = {
  template: `
    <v-ons-page>
      <custom-toolbar backLabel="Back">
        {{ folder }}
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
      folders: ['none', 'default', 'slide-ios', 'slide-md', 'lift-ios', 'lift-md', 'fade-ios', 'fade-md']
    };
  },
  methods: {
    transition(name) {
      this.$store.commit('navigator/options', {
        // Sets folders
        folder: name,
        // Resets default options
        callback: () => this.$store.commit('navigator/options', {})
      });

      this.$store.commit('navigator/push', {
        extends: transitionPage,
        data() {
          return {
            folder: name
          }
        }
      });
    }
  }
};
</script>
