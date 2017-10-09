<template>
  <v-ons-page>
    <custom-toolbar v-bind="toolbarInfo"></custom-toolbar>
    <v-ons-list>
      <v-ons-list-item v-for="book in books" :key="book.label"
        modifier="chevron"
        @click="push(book.component, book.label)"
      >
        {{ book.label }}
      </v-ons-list-item>
    </v-ons-list>
  </v-ons-page>
</template>

<script>
import InfiniteScroll from './InfiniteScroll.vue'
export default {
  data() {
    return {
      books: [
          {
              component: InfiniteScroll,
              label: 'none'
          },
          ]
    };
  },
  methods: {
    push(page, key) {
      this.$store.commit('navigator/push', {
        extends: page,
        data() {
          return {
            toolbarInfo: {
              backLabel: 'Home',
              title: key
            }
          }
        }
      });
    }
  }
};
</script>
