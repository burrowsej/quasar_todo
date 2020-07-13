<template>
  <q-layout view="hHh lpR fFf">
    <q-header elevated>
      <q-toolbar>
        <q-toolbar-title class="absolute-center">
          ToDo App
        </q-toolbar-title>

      </q-toolbar>
    </q-header>

    <q-drawer
      breakpoint="767"
      v-model="leftDrawerOpen"
      show-if-above
      bordered
      :width="250"
      content-class="bg-primary"
    >
      <q-list dark>
        <q-item-label header>Navigation</q-item-label>
        <EssentialLink
          v-for="nav in navs"
          :key="nav.label"
          v-bind="nav"
          class="text-grey-5"
        />
      </q-list>
    </q-drawer>

    <q-page-container align="center">
      <router-view />
    </q-page-container>

     <q-footer>
        <q-toolbar>
          <q-tabs class="absolute-center">
            <q-route-tab
            v-for="nav in navs"
            :key="nav.label"
            :to="nav.to"
            :icon="nav.icon"
            :label="nav.label" />
          </q-tabs>
        </q-toolbar>
      </q-footer>
  </q-layout>
</template>

<script>
import EssentialLink from 'components/EssentialLink.vue'

export default {
  name: 'MainLayout',

  components: {
    EssentialLink
  },

  data () {
    return {
      leftDrawerOpen: false,
      navs: [
        {
          label: 'Todo',
          icon: 'list',
          to: '/'
        },
        {
          label: 'Settings',
          icon: 'settings',
          to: '/settings'
        }
      ]
    }
  }
}
</script>

<style lang="scss">
  @media screen and (min-width: 768px) {
    .q-footer {
      display: none;
    }
  }

  .q-drawer {
    .q-router-link--exact-active {
      color: white !important;
    }
  }
  
</style>