<template>
  <nav>
    <v-container>
      <v-navigation-drawer v-model="drawer" absolute temporary>
        <v-list nav dense>
          <v-list-item
            v-model="group"
            v-for="itemTab in items"
            :key="itemTab.name"
            active-class="tab-active-mb"
            :to="itemTab.path == '#' ? '' : itemTab.path"
          >
            <v-list-item-icon>
              <v-icon>{{ itemTab.icon }}</v-icon>
            </v-list-item-icon>

            <v-list-item-title>
              <v-list-item-title>{{ itemTab.title }}</v-list-item-title>
            </v-list-item-title>
          </v-list-item>
        </v-list>
      </v-navigation-drawer>
      <!-- <v-navigation-drawer
        v-model="drawer"
        absolute
        temporary
        class="d-lg-none"
      >
        <v-tabs
          vertical
          v-model="tab"
          :optional="optional"
          color="red"
          active-class="tab-active-mb"
        >
          <v-tab
            v-for="itemTab in items"
            :key="itemTab.name"
            :to="itemTab.path == '#' ? '' : itemTab.path"
            ><v-icon left>{{ itemTab.icon }}</v-icon
            >{{ itemTab.title }}</v-tab
          >
        </v-tabs>
      </v-navigation-drawer>-->
      <v-row justify="center" align="center">
        <v-toolbar style="background-color: transparent;" flat>
          <v-app-bar-nav-icon class="d-lg-none" @click.stop="drawer = !drawer"></v-app-bar-nav-icon>
          <v-toolbar-title>AloneCoding</v-toolbar-title>
          <v-spacer></v-spacer>

          <v-toolbar-items class="d-none d-sm-flex">
            <v-tabs
              v-model="tab"
              :optional="optional"
              color="red"
              active-class="tab-active"
              icons-and-text
              background-color="transparent"
            >
              <v-tab v-for="item in items" :key="item.name" :to="item.path == '#' ? '' : item.path">
                {{ item.title }}
                <v-icon>{{ item.icon }}</v-icon>
              </v-tab>
            </v-tabs>
          </v-toolbar-items>
        </v-toolbar>
      </v-row>
    </v-container>
  </nav>
</template>

<script>
export default {
  data() {
    return {
      drawer: false,
      optional: true,
      tab: null,
      items: [
        {
          name: "Home",
          icon: "fas fa-home",
          title: "หน้าแรก",
          path: "/"
        },
        {
          name: "Profile",
          icon: "fas fa-user",
          title: "โปรไฟล์",
          path: "/profile"
        },
        {
          name: "Awards",
          icon: "fas fa-award",
          title: "ผลงาน",
          path: "/awards"
        },
        {
          name: "Covid",
          icon: "fas fa-plus-circle",
          title: "สถานการณ์โควิด",
          path: "/covid"
        }
        // {
        //   name: "About",
        //   icon: "fas fa-info",
        //   title: "เกี่ยวกับ",
        //   path: "/about"
        // }
      ]
    };
  },
  watch: {
    group() {
      console.log("Hello");
      this.drawer = false;
    }
  }
};
</script>

<style>
.nav {
  color: white;
}
.tab-active {
  border-bottom: solid 2px red;
}
.tab-active-mb {
  border-left: solid 3px red;
}
</style>
