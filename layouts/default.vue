<template>
  <v-app>
    <v-navigation-drawer
      v-model="drawer"
      fixed
      app
      :width="250"
      mobile-breakpoint="1260"
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
      <!-- greetings -->
      <div class="greeting ml-2">
        <div>
          <svg
            class="hamburger"
            @click.stop="drawer = !drawer"
            width="24"
            height="24"
            viewBox="0 0 24 24"
            fill="none"
            xmlns="http://www.w3.org/2000/svg"
          >
            <g clip-path="url(#clip0_1630_86626)">
              <path
                d="M3 4H21V6H3V4ZM3 11H21V13H3V11ZM3 18H21V20H3V18Z"
                fill="#000831"
              />
            </g>
            <defs>
              <clipPath id="clip0_1630_86626">
                <rect width="24" height="24" fill="white" />
              </clipPath>
            </defs>
          </svg>
        </div>
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

      <v-menu :nudge-bottom="5" offset-y>
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
        <v-list class="dropdown__list nav__list">
          <nuxt-link to="/profile">
            <v-list-item class="dropdown__list-item">
              <v-list-item-icon>
                <svg
                  width="24"
                  height="25"
                  viewBox="0 0 24 25"
                  fill="none"
                  xmlns="http://www.w3.org/2000/svg"
                >
                  <g clip-path="url(#clip0_1485_89653)">
                    <path
                      d="M20 22.5H4V20.5C4 19.1739 4.52678 17.9021 5.46447 16.9645C6.40215 16.0268 7.67392 15.5 9 15.5H15C16.3261 15.5 17.5979 16.0268 18.5355 16.9645C19.4732 17.9021 20 19.1739 20 20.5V22.5ZM12 13.5C11.2121 13.5 10.4319 13.3448 9.7039 13.0433C8.97595 12.7417 8.31451 12.2998 7.75736 11.7426C7.20021 11.1855 6.75825 10.5241 6.45672 9.7961C6.15519 9.06815 6 8.28793 6 7.5C6 6.71207 6.15519 5.93185 6.45672 5.2039C6.75825 4.47595 7.20021 3.81451 7.75736 3.25736C8.31451 2.70021 8.97595 2.25825 9.7039 1.95672C10.4319 1.65519 11.2121 1.5 12 1.5C13.5913 1.5 15.1174 2.13214 16.2426 3.25736C17.3679 4.38258 18 5.9087 18 7.5C18 9.0913 17.3679 10.6174 16.2426 11.7426C15.1174 12.8679 13.5913 13.5 12 13.5Z"
                      fill="#666B70"
                    />
                  </g>
                  <defs>
                    <clipPath id="clip0_1485_89653">
                      <rect
                        width="24"
                        height="24"
                        fill="white"
                        transform="translate(0 0.5)"
                      />
                    </clipPath>
                  </defs>
                </svg>
              </v-list-item-icon>
              <v-list-item-content>
                <v-list-item-title class="dropdown__list-title"
                  >My Profile</v-list-item-title
                >
              </v-list-item-content>
            </v-list-item>
          </nuxt-link>
          <v-list-item class="dropdown__list-item">
            <v-list-item-icon>
              <svg
                width="24"
                height="25"
                viewBox="0 0 24 25"
                fill="none"
                xmlns="http://www.w3.org/2000/svg"
              >
                <path
                  fill-rule="evenodd"
                  clip-rule="evenodd"
                  d="M7.5 4.25C7.10218 4.25 6.72064 4.40804 6.43934 4.68934C6.15804 4.97064 6 5.35218 6 5.75V19.25C6 19.6478 6.15804 20.0294 6.43934 20.3107C6.72064 20.592 7.10218 20.75 7.5 20.75H13.5C13.8978 20.75 14.2794 20.592 14.5607 20.3107C14.842 20.0294 15 19.6478 15 19.25V15.5C15 15.3011 15.079 15.1103 15.2197 14.9697C15.3603 14.829 15.5511 14.75 15.75 14.75C15.9489 14.75 16.1397 14.829 16.2803 14.9697C16.421 15.1103 16.5 15.3011 16.5 15.5V19.25C16.5 20.0456 16.1839 20.8087 15.6213 21.3713C15.0587 21.9339 14.2956 22.25 13.5 22.25H7.5C6.70435 22.25 5.94129 21.9339 5.37868 21.3713C4.81607 20.8087 4.5 20.0456 4.5 19.25V5.75C4.5 4.95435 4.81607 4.19129 5.37868 3.62868C5.94129 3.06607 6.70435 2.75 7.5 2.75H13.5C14.2956 2.75 15.0587 3.06607 15.6213 3.62868C16.1839 4.19129 16.5 4.95435 16.5 5.75V9.5C16.5 9.69891 16.421 9.88968 16.2803 10.0303C16.1397 10.171 15.9489 10.25 15.75 10.25C15.5511 10.25 15.3603 10.171 15.2197 10.0303C15.079 9.88968 15 9.69891 15 9.5V5.75C15 5.35218 14.842 4.97064 14.5607 4.68934C14.2794 4.40804 13.8978 4.25 13.5 4.25H7.5ZM12.53 8.97C12.6705 9.11063 12.7493 9.30125 12.7493 9.5C12.7493 9.69875 12.6705 9.88937 12.53 10.03L10.81 11.75H21.75C21.9489 11.75 22.1397 11.829 22.2803 11.9697C22.421 12.1103 22.5 12.3011 22.5 12.5C22.5 12.6989 22.421 12.8897 22.2803 13.0303C22.1397 13.171 21.9489 13.25 21.75 13.25H10.81L12.53 14.97C12.6037 15.0387 12.6628 15.1215 12.7038 15.2135C12.7448 15.3055 12.7668 15.4048 12.7686 15.5055C12.7704 15.6062 12.7518 15.7062 12.7141 15.7996C12.6764 15.893 12.6203 15.9778 12.549 16.049C12.4778 16.1203 12.393 16.1764 12.2996 16.2141C12.2062 16.2518 12.1062 16.2704 12.0055 16.2686C11.9048 16.2668 11.8055 16.2448 11.7135 16.2038C11.6215 16.1628 11.5387 16.1037 11.47 16.03L8.47 13.03C8.32955 12.8894 8.25066 12.6988 8.25066 12.5C8.25066 12.3012 8.32955 12.1106 8.47 11.97L11.47 8.97C11.6106 8.82955 11.8012 8.75066 12 8.75066C12.1988 8.75066 12.3894 8.82955 12.53 8.97Z"
                  fill="#666B70"
                />
              </svg>
            </v-list-item-icon>
            <v-list-item-content>
              <v-list-item-title class="dropdown__list-title"
                >Log Out</v-list-item-title
              >
            </v-list-item-content>
          </v-list-item>
        </v-list>
      </v-menu>
    </v-app-bar>

    <!-- page content -->
    <v-main app>
      <Nuxt />
    </v-main>

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
      width: 512,
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
  mounted() {
    var nx = window.innerWidth;
    if (nx <= 540) {
      this.width = "100vw";
    }
    window.addEventListener("resize", function (event) {
      var w = window.innerWidth;
      nx = w;
    });
    $(window).resize(() => {
      if (nx <= 540) {
        this.width = "100vw";
      } else {
        this.width = 512;
      }
    });
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
};
</script>

<style scoped lang="scss">
/* scroller end */
div.greeting {
  line-height: 2.5rem;
  display: flex;
  align-items: center;
  grid-gap: 7px;
  svg {
    cursor: pointer;
  }

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
  border-radius: 50%;
  box-shadow: 0px 4px 5px 4px rgba(0, 0, 0, 0.04);
  margin-right: 6px;
  cursor: pointer;
  width: 56px;
  height: 56px;
  img {
    width: 100%;
    height: 100%;
    object-fit: cover;
    border-radius: 50%;
    border: 3px solid #fff;
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