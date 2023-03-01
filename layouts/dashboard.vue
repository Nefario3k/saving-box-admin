<template>
  <v-app>
    <v-navigation-drawer
      v-model="drawer"
      fixed
      app
      :width="250"
      class="custom-scroller"
    >
      <DashboardMenu />
    </v-navigation-drawer>

    <!-- app bar -->
    <v-app-bar
      color="#fff"
      elevate-on-scroll
      elevation="1"
      fixed
      :height="70"
      app
      class="pe-3"
    >
      <!-- logo -->
      <!-- <div class="d-none d-sm-block">
        <img src="/images/savingbox-logo.png" alt="" />
        <span style="color: #4169e1; font-size: 2.1rem; font-weight: 600"
          >SavingsBox</span
        >
        <v-btn icon @click.stop="drawer = !drawer">
          <v-icon style="color: rgba(65, 105, 225, 1)"
            >mdi-{{ `chevron-${drawer ? "left" : "right"}` }}</v-icon
          >
        </v-btn>
      </div> -->
      <div class="d-md-none">
        <v-icon style="font-size: 3.5rem" @click.stop="drawer = !drawer"
          >mdi-menu</v-icon
        >
      </div>

      <!-- greetings -->
      <div class="greeting ml-2">
        <span class="user-greeting">Admin</span>
      </div>

      <!-- <v-toolbar-title v-text="clipped" /> -->

      <v-spacer />

      <span
        class="notification-icon-container"
        @click="showNotifications = true"
      >
        <svg
          width="100%"
          height="100%"
          viewBox="0 0 48 48"
          fill="none"
          xmlns="http://www.w3.org/2000/svg"
        >
          <circle cx="24" cy="24" r="24" fill="#ECF1FF" />
          <path
            d="M17.0598 20.2118C17.4527 16.6754 20.4419 14 24 14V14C27.5581 14 30.5473 16.6754 30.9402 20.2118L31.2549 23.0445C31.3069 23.5123 31.3329 23.7462 31.3721 23.9758C31.5128 24.8011 31.7822 25.5993 32.1705 26.3411C32.2785 26.5475 32.3995 26.7492 32.6417 27.1528L33.4326 28.471C34.2384 29.8139 34.6412 30.4854 34.354 30.9927C34.0668 31.5 33.2837 31.5 31.7176 31.5H16.2824C14.7163 31.5 13.9332 31.5 13.646 30.9927C13.3588 30.4854 13.7616 29.8139 14.5674 28.471L15.3583 27.1528C15.6005 26.7492 15.7215 26.5475 15.8295 26.3411C16.2178 25.5993 16.4872 24.8011 16.6279 23.9758C16.6671 23.7462 16.6931 23.5123 16.7451 23.0445L17.0598 20.2118Z"
            stroke="#4169E1"
            stroke-width="2"
          />
          <path
            d="M20.3778 32.0073C20.5914 32.9376 21.0622 33.7596 21.7171 34.3459C22.3721 34.9322 23.1745 35.25 24 35.25C24.8255 35.25 25.6279 34.9322 26.2829 34.3459C26.9378 33.7596 27.4086 32.9376 27.6222 32.0073"
            stroke="#4169E1"
            stroke-width="2"
            stroke-linecap="round"
          />
        </svg>
        <span class="notification-available"></span>
      </span>

      <v-menu offset-y>
        <template v-slot:activator="{ on, attrs }">
          <div class="d-flex align-items-center" v-bind="attrs" v-on="on">
            <div class="user-icon-container">
              <img src="/images/temporary/profile.jpg" alt="" />
            </div>
            <div class="adminName">
              <span>Administrator</span>
              <i
                class="fa-solid fa-chevron-down"
                style="font-size: 1.7rem !important"
              ></i>
            </div>
          </div>
        </template>
        <v-list>
          <v-list-item v-for="(item, index) in items" :key="index" link>
            <v-list-item-icon>
              <!-- <v-icon v-text="item.icon"></v-icon> -->
              <i :class="item.icon"></i>
            </v-list-item-icon>
            <v-list-item-content>
              <v-list-item-title>{{ item.title }}</v-list-item-title>
            </v-list-item-content>
          </v-list-item>
        </v-list>
      </v-menu>
    </v-app-bar>

    <!-- page content -->
    <v-main app>
      <Nuxt />
    </v-main>

    <v-navigation-drawer
      v-model="rightDrawer"
      :right="true"
      :width="width"
      temporary
      fixed
    >
      <v-list>
        <!-- <v-list-item @click.native="right = !right">
          <v-list-item-action>
            <v-icon light> mdi-repeat </v-icon>
          </v-list-item-action>
          <v-list-item-title>Switch drawer (click me)</v-list-item-title>
        </v-list-item> -->
      </v-list>
    </v-navigation-drawer>
    <AssetsRightDrawer
      :showDrawer="showNotifications"
      @closeDrawer="showNotifications = false"
    >
      <DashboardNotifications />
    </AssetsRightDrawer>
  </v-app>
</template>

<script>
export default {
  data() {
    return {
      drawer: true,
      miniVariant: false,
      right: true,
      rightDrawer: false,
      showNotifications: false,
      faIcon: "fa-solid fa-gift menu-icon",
      title: "Vuetify.js",
      items: [
        { title: "My Profile", icon: "fa-solid fa-user menu-icon" },
        { title: "My Savings", icon: "fa-solid fa-piggy-bank menu-icon" },
        {
          title: "Investment",
          icon: "fa-solid fa-arrow-up-right-dots menu-icon",
        },
        {
          title: "Jollification",
          icon: "fa-solid fa-champagne-glasses menu-icon",
        },
        { title: "Loan", icon: "fa-solid fa-hand-holding-dollar menu-icon" },
        { title: "Referral", icon: "fa-solid fa-gift menu-icon" },
        { title: "Log Out", icon: "fa-solid fa-right-from-bracket menu-icon" },
      ],
    };
  },
};
</script>

<style scoped lang="scss">
/* scroller end */
div.greeting {
  line-height: 2.5rem;

  .user-greeting {
    color: var(--label-third-color);
    font-weight: 500;
    font-size: 2rem;
  }

  .user-name {
    color: rgba(65, 105, 225, 1);
    font-weight: 600;
    font-size: 2.4rem;
    /* margin-left: 10px; */
  }
}

.notification-icon-container {
  width: 48px;
  height: 48px;
  cursor: pointer;
  text-align: center;
  position: relative;
  margin-right: 47px;
}

.notification-icon {
  font-size: 25px;
}

.notification-available {
  padding: 4px;
  background-color: red;
  border-radius: 10px;
  position: absolute;
  top: 1px;
  right: 7px;
}

.user-icon-container {
  background-color: transparent;
  border-radius: 50px;
  box-shadow: 0px 4px 5px 4px rgba(0, 0, 0, 0.04);
  border: 4px solid #fff;
  margin-right: 6px;
  cursor: pointer;
  width: 56px;
  height: 56px;
  overflow: hidden;
  img {
    width: 56px;
    height: 56px;
    object-fit: contain;
    border-radius: 50px;
  }
}
.adminName {
  display: flex;
  align-items: center;
  gap: 12px;
  span {
    font-weight: 500;
    font-size: 1.8rem;
    color: var(--black2);
  }
}

.user-icon-container div.v-list-item__title {
  /* color: red !important; */
  font-size: 1.8rem;
  line-height: 2.4rem;
  color: #666b70;
}
</style>