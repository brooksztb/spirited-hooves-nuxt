<template>
  <v-app dark>
    <v-navigation-drawer
      v-model="drawer"
      :mini-variant="miniVariant"
      :clipped="clipped"
      class="primary"
      app
    >
      <v-list>
        <v-list-item
          v-for="(item, i) in items"
          :key="i"
          :to="item.to"
          router
          exact
        >
          <v-list-item-action>
            <v-icon>{{ item.icon }}</v-icon>
          </v-list-item-action>
          <v-list-item-content>
            <v-list-item-title v-text="item.title" />
          </v-list-item-content>
        </v-list-item>
      </v-list>
    </v-navigation-drawer>
    <v-app-bar :clipped-left="clipped" class="primary" fixed app>
      <v-app-bar-nav-icon
        @click.stop="drawer = !drawer"
        class="hidden-md-and-up"
      />
      <v-toolbar-title class="nav-logo-container pr-4" to="/">
        <img
          class="nav-logo hidden-xs-only"
          src="@/static/spiritedhooves-logo.svg"
          alt=""
        />
        {{ title }}
      </v-toolbar-title>
      <v-btn
        v-for="(item, i) in items"
        :key="i"
        :to="item.to"
        class="hidden-sm-and-down"
        text
        router
        exact
      >
        <v-icon class="pr-1">{{ item.icon }}</v-icon>
        {{ item.title }}
      </v-btn>
    </v-app-bar>
    <v-content>
      <v-container>
        <nuxt />
      </v-container>
    </v-content>
    <v-footer :fixed="fixed" app>
      <span>&copy; 2019</span>
    </v-footer>
  </v-app>
</template>

<script>
export default {
  data() {
    return {
      clipped: false,
      drawer: false,
      fixed: false,
      items: [
        {
          icon: 'mdi-home',
          title: 'Home',
          to: '/'
        },
        {
          icon: 'mdi-information',
          title: 'About',
          to: '/about'
        }
      ],
      miniVariant: false,
      title: 'Spirited Hooves'
    }
  }
}
</script>

<style lang="scss" scoped>
.nav-logo-container {
  cursor: pointer;
}
.nav-logo {
  width: 75px;
  height: 75px;
  vertical-align: middle;
}
</style>
