<template>
  <v-app light>

    <v-app-bar app>
      <v-toolbar-title v-text="title" />
      <v-spacer />
      <v-app-bar-nav-icon @click.stop="drawer = !drawer" />
    </v-app-bar>

    <v-navigation-drawer v-model="drawer" app right>
      <v-list>
        <v-list-item v-for="(item, i) in items" :key="i" :to="item.to" router exact>
          <v-list-item-action>
            <v-icon>{{ item.icon }}</v-icon>
          </v-list-item-action>
          <v-list-item-content>
            <v-list-item-title v-text="item.title" />
          </v-list-item-content>
        </v-list-item>
      </v-list>
    </v-navigation-drawer>

    <v-main>
      <nuxt />
    </v-main>
    
    <v-footer app>
      <span>{{ new Date().getFullYear() }} - The information on this site is not a substitute for legal advice.</span>
    </v-footer>
  </v-app>
</template>

<script>
export default {
  data () {
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
          icon: 'mdi-frequently-asked-questions',
          title: 'FAQs',
          to: '/faq'
        },
        {
          icon: 'mdi-map',
          title: 'Cross Border Zone',
          to: '/map'
        },
        {
          icon: 'mdi-clipboard-check',
          title: 'Permit Application',
          to: '/permit'
        },
        {
          icon: 'mdi-text-box-multiple-outline',
          title: 'Public Health Orders',
          to: '/orders'
        }
      ],
      miniVariant: false,
      right: true,
      title: 'NSW Vic Border Closure'
    }
  }
}
</script>
