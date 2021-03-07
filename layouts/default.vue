<template>
  <v-app>
    <header>
      <div class="wrap">
        <div class="site-title">
          <a href="/">
            <h2>ここに良い感じのタイトルをつけたい</h2>
          </a>
        </div>
      </div>
    </header>

    <v-main>
      <v-container>
        <v-row>
          <!-- <v-col cols=12 lg=12 md=12 sm=12 align="center" class="mt-5 mb-10">
          <h2>ここに良い感じのタイトルをつけたい</h2>
        </v-col> -->
          <v-col cols="12" xs="8" md="12" class="ms-auto">
            <nuxt />
          </v-col>
        </v-row>
      </v-container>
    </v-main>
    <v-navigation-drawer v-model="rightDrawer" :right="right" temporary fixed>
      <v-list>
        <v-list-item @click.native="right = !right">
          <v-list-item-action>
            <v-icon light>
              mdi-repeat
            </v-icon>
          </v-list-item-action>
          <v-list-item-title>Switch drawer (click me)</v-list-item-title>
        </v-list-item>
      </v-list>
    </v-navigation-drawer>
    <v-footer :absolute="!fixed" app>
      <span>&copy; {{ new Date().getFullYear() }}</span>
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
          icon: "mdi-apps",
          title: "Welcome",
          to: "/"
        },
        {
          icon: "mdi-chart-bubble",
          title: "Inspire",
          to: "/inspire"
        }
      ],
      miniVariant: false,
      right: true,
      rightDrawer: false,
      title: "Vuetify.js"
    };
  }
};
</script>

<style lang="scss">
a {
  text-decoration: none;
}
header {
  background: url("~/assets/img/header.jpg") no-repeat 50% 50%;
  display: block;
  position: relative;
  .wrap {
    margin-left: auto;
    margin-right: auto;
    text-align: center;
    padding: 10%;
    .site-title {
      position: relative;
      h2 {
        color: #fff;
      }
    }
  }
  .wrap::before {
    content: "";
    display: block;
    height: 100%;
    position: absolute;
    top: 0;
    left: 0;
    width: 100%;
    z-index: 0;
    background-color: rgba(59, 86, 103, 0.7);
  }
}
</style>
