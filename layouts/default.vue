<template>
  <v-app color="#fff">
    <!-- left side panel  -->
    <NavigationPanel ref="panel" />
    <!-- app bar -->
    <NavigationBar @showNav="showNav" @showNotifications="showNotifications" />

    <!-- page content -->
    <v-main app>
      <Nuxt />
    </v-main>

    <AssetsRightDrawer
      :showDrawer="showSideNoti"
      @closeDrawer="showSideNoti = false"
    >
      <DashboardNotifications />
    </AssetsRightDrawer>
  </v-app>
</template>

<script>
export default {
  data() {
    return {
      showSideNoti: false,
    };
  },
  head: {
    script: [
      {
        src: "/scripts/jquery-3.3.1.min.js",
        type: "text/javascript",
        body: true,
      },
    ],
  },
  methods: {
    showNav() {
      this.$refs.panel.showPanel();
    },
    showNotifications() {
      this.showSideNoti = true;
    },
  },
};
</script>

