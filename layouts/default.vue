<template>
  <v-app dark>
    <v-app-bar
      absolute
      app
    >
      <v-toolbar-title  ><n-link to="/" v-text="title" class="flat"/></v-toolbar-title>
      <v-spacer />
      <v-btn
        icon
        @click.stop="rightDrawer = !rightDrawer"
      >
        <v-icon>mdi-menu</v-icon>
      </v-btn>
    </v-app-bar>
    <v-content>
      <nuxt />
    </v-content>
    <v-navigation-drawer
      v-model="rightDrawer"
      right
      temporary
      fixed
      class="sidemenu"
    >
      <v-list>
        <v-list-item
          v-for="(item, index) in rightMenu"
          :key="index"
          :to="item.path">
          <v-list-item-title 
          >{{item.title.toUpperCase()}}
          </v-list-item-title>
        </v-list-item>
      </v-list>
    </v-navigation-drawer>

    <v-divider></v-divider>
    <v-footer
      padless
      class="white"
    >
      <v-container>
        <v-row>
          <v-col v-for="(group, key) in links" :key="key">
            <v-list dense flat>
              <v-subheader class="subtitle-1">{{key.toUpperCase()}}</v-subheader>
              <v-list-item
                v-for="(link, i) in group"
                :key="i"
                :to="link.link"
                target="_blank"
                flat
              >
                <v-list-item-icon>
                  <v-icon v-text="link.icon"></v-icon>
                </v-list-item-icon>
                <v-list-item-content  class="text-left">
                  <v-list-item-title v-text="link.name"></v-list-item-title>
                  <v-list-item-subtitle v-text="link.text"></v-list-item-subtitle>
                </v-list-item-content>
              </v-list-item>
            </v-list>
          </v-col>
        </v-row>
        <v-row>
          <v-col class="text-center">
            2019 — <strong>{{title}}</strong>
          </v-col>
        </v-row>
      </v-container>
    </v-footer>
  </v-app>
</template>

<script>
import links from '~/src/links.json'
export default {
  data () {
    return {
      rightDrawer: false,
      title: 'Kakimotoのポートフォリオサイト',
      rightMenu: [
        {
          title: 'top',
          path: '/'
        },{
          title: 'about',
          path: '/about'
        },{
          title: 'posts',
          path: '/posts'
        }
      ],
      links: links
    }
  }
}
</script>
<style lang="scss">
.v-list-item:hover{
  background-color: #d1d1d1;
}
.sidemenu{
  z-index: 2000;
}
* {
    box-sizing: border-box;
}
a.flat{
  text-decoration: none;
  color:inherit;
}
</style>