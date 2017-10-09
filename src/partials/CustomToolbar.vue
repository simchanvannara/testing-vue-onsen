<template>
  <v-ons-toolbar>
    <div class="left" v-if="backLabel">
      <slot name="left">
        <v-ons-back-button v-if="backLabel">
          {{ backLabel }}
        </v-ons-back-button>
      </slot>
    </div>
    <div class="left" v-if="!backLabel"><slot name="right"></slot></div>
    <div class="center"><slot>{{ title }}</slot></div>
    
  </v-ons-toolbar>
</template>

<script>
export default {
  props: ['title', 'backLabel']
};
</script>
