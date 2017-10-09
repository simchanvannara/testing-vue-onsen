<template>
  <v-ons-page modifier="white">
    <!--<div class="profile-pic">
      <img src="../assets/Pkachhuk.png">
    </div>-->

    <v-ons-list>
      <v-ons-list-item v-for="page of pages" :key="page.label"
      @click="push(page.component, page.label)"
      >
        <div class="left">
          <v-ons-icon fixed-width class="list-item__icon" :icon="page.icon"></v-ons-icon>
        </div>
        <div class="center">
          {{ page.label }}
        </div>
      </v-ons-list-item>
    </v-ons-list>
  </v-ons-page>
</template>

<script>
import Search from './Search.vue';
import Book from './Book.vue';
import Folder from './Folder.vue';
import Favourite from './Favourite.vue';
import Profile from './Profile.vue';
import AboutUs from './AboutUs.vue';

export default {
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
  },
  data() {
    return {
      pages: [
        {
          component: Search,
          label: 'Search',
          icon: 'ion-ios-search-strong'
        },
        {
          component: Book,
          label: 'Book',
          icon: 'ion-ios-book'
        },
        {
          component: Folder,
          label: 'Folder',
          icon: 'ion-ios-folder'
        },
        {
          component: Favourite,
          label: 'Favourite',
          icon: 'ion-star'
        },
        {
          component: Profile,
          label: 'Profile',
          icon: 'ion-person'
        },
        {
          component: AboutUs,
          label: 'About Us',
          icon: 'ion-person'
        },
        {
          label: 'Log Out',
          icon: 'ion-power'
        }
      ]
    };
  }
};
</script>

<style scoped>
.profile-pic {
  width: 100%;
  background-color: #fff;
  border-bottom: 1px solid #DDD;
  color: rgba(0, 0, 0, .56);
  padding-bottom: 8px;
}
.page--material .profile-pic {
  background-color: #f6f6f6;
}

.profile-pic > img {
  display: block;
  max-width: 100%;
}
</style>

<style>
.page--material__background.page--white__background {
  background-color: #fff;
}
</style>
