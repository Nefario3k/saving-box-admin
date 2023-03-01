<template>
  <div style="position: relative">
    <!-- <v-overlay
      z-index="99"
      :opacity="0.4"
      :value="showDrawer"
      @click="closeDrawer()"
    ></v-overlay> -->
    <v-navigation-drawer
      style="z-index: 100"
      v-model="showDrawer"
      :right="true"
      :width="width"
      temporary
      fixed
      class="adminPanel relative"
    >
      <!-- create auto savings form -->
      <v-app-bar
        style="margin-left: 1px"
        color="#fff"
        :elevation="elevation"
        fixed
        :height="50"
      >
        <div class="text-right">
          <svg
            @click="closeDrawer()"
            width="30"
            height="30"
            viewBox="0 0 30 30"
            fill="none"
            xmlns="http://www.w3.org/2000/svg"
          >
            <path
              d="M22.5 7.5L7.5 22.5"
              stroke="#FF0000"
              stroke-width="1.5"
              stroke-linecap="round"
              stroke-linejoin="round"
            />
            <path
              d="M7.5 7.5L22.5 22.5"
              stroke="#FF0000"
              stroke-width="1.5"
              stroke-linecap="round"
              stroke-linejoin="round"
            />
          </svg>
        </div>
      </v-app-bar>

      <div
        ref="myDiv"
        class="p-0 mt-2 right-drawer-container"
        @scroll="handleScroll"
      >
        <div class="headerTag">
          <div class="right-drawer-title">
            <div class="intro">
              <svg
                width="28"
                height="28"
                viewBox="0 0 28 28"
                fill="none"
                xmlns="http://www.w3.org/2000/svg"
              >
                <g clip-path="url(#clip0_590_82190)">
                  <path
                    d="M13.9999 2.33301C20.4434 2.33301 25.6666 7.55618 25.6666 13.9997C25.6666 20.4432 20.4434 25.6663 13.9999 25.6663C7.55642 25.6663 2.33325 20.4432 2.33325 13.9997H4.66659C4.66659 19.154 8.84559 23.333 13.9999 23.333C19.1543 23.333 23.3333 19.154 23.3333 13.9997C23.3333 8.84534 19.1543 4.66634 13.9999 4.66634C10.7916 4.66634 7.96125 6.28451 6.28242 8.74967H9.33325V11.083H2.33325V4.08301H4.66659V6.99967C6.79459 4.16467 10.1838 2.33301 13.9999 2.33301ZM15.1666 8.16634V13.5155L18.9501 17.299L17.2993 18.9498L12.8333 14.4815V8.16634H15.1666Z"
                    fill="#000831"
                  />
                </g>
                <defs>
                  <clipPath id="clip0_590_82190">
                    <rect width="28" height="28" fill="white" />
                  </clipPath>
                </defs>
              </svg>
              <h1 class="">Activity Details</h1>
            </div>

            <div class="local__data">
              <div>
                <span>IP Address:</span>
                <span class="activityIp">192.158.1.38</span>
              </div>
              <span class="dActivity">Download Activity</span>
            </div>
          </div>
        </div>
        <v-divider class="divider"></v-divider>
        <div class="timeline">
          <v-timeline align-top dense>
            <v-timeline-item
              v-for="(item, i) in 20"
              :key="i"
              color="transparent"
            >
              <template v-if="i % 2" v-slot:icon>
                <svg
                  width="32"
                  height="32"
                  viewBox="0 0 32 32"
                  fill="none"
                  xmlns="http://www.w3.org/2000/svg"
                >
                  <circle
                    cx="16"
                    cy="16"
                    r="15.5"
                    fill="white"
                    stroke="#D0D0D0"
                  />
                  <g clip-path="url(#clip0_606_81654)">
                    <path
                      d="M20.6735 21.333L8.50772 21.333C8.28465 21.333 8.07073 21.2696 7.913 21.1567C7.75527 21.0439 7.66667 20.8908 7.66667 20.7312L7.66667 11.1015C7.66667 10.9419 7.75528 10.7888 7.913 10.6759C8.07073 10.5631 8.28466 10.4997 8.50772 10.4997L20.6735 10.4997C20.8119 10.4997 20.9482 10.5241 21.0703 10.5708C21.1924 10.6175 21.2964 10.6851 21.3733 10.7675L25.8586 15.5823C25.9508 15.6812 26 15.7974 26 15.9163C26 16.0352 25.9508 16.1515 25.8586 16.2504L21.3733 21.0652C21.2964 21.1476 21.1924 21.2151 21.0703 21.2619C20.9482 21.3086 20.8119 21.333 20.6735 21.333ZM12.713 16.5182L18.6003 16.5182L18.6003 15.3145L12.713 15.3145L12.713 16.5182Z"
                      fill="#1C861C"
                    />
                  </g>
                  <defs>
                    <clipPath id="clip0_606_81654">
                      <rect
                        width="20"
                        height="14.1667"
                        fill="white"
                        transform="translate(26 23) rotate(-180)"
                      />
                    </clipPath>
                  </defs>
                </svg>
              </template>
              <template v-else v-slot:icon>
                <svg
                  width="32"
                  height="32"
                  viewBox="0 0 32 32"
                  fill="none"
                  xmlns="http://www.w3.org/2000/svg"
                >
                  <circle
                    cx="16"
                    cy="16"
                    r="15.5"
                    fill="white"
                    stroke="#D0D0D0"
                  />
                  <g clip-path="url(#clip0_590_82207)">
                    <path
                      d="M16.75 11.7151L20.285 15.2509L12.035 23.5001H8.5V19.9642L16.75 11.7151ZM17.9283 10.5367L19.6958 8.7684C19.8521 8.61218 20.064 8.52441 20.285 8.52441C20.506 8.52441 20.7179 8.61218 20.8742 8.7684L23.2317 11.1259C23.3879 11.2822 23.4757 11.4941 23.4757 11.7151C23.4757 11.936 23.3879 12.148 23.2317 12.3042L21.4633 14.0717L17.9283 10.5367Z"
                      fill="#666B70"
                    />
                  </g>
                  <defs>
                    <clipPath id="clip0_590_82207">
                      <rect
                        width="20"
                        height="20"
                        fill="white"
                        transform="translate(6 6)"
                      />
                    </clipPath>
                  </defs>
                </svg>
              </template>

              <div class="timeline__wrapper">
                <h3>
                  <span class="name">John Doe</span> Declined a loan request
                  from
                  <span class="admin">Maxwell Hima</span>
                </h3>
                <span class="timeline__date"
                  >Nov 7, 2022 at 09:35 AM Via Web</span
                >
              </div>
            </v-timeline-item>

            <!-- bottom  -->
            <v-timeline-item color="transparent">
              <template v-slot:icon>
                <svg
                  style="cursor: pointer"
                  width="30"
                  height="30"
                  viewBox="0 0 30 30"
                  fill="none"
                  xmlns="http://www.w3.org/2000/svg"
                >
                  <rect
                    x="0.5"
                    y="0.5"
                    width="29"
                    height="29"
                    rx="4.5"
                    fill="white"
                    stroke="#D0D0D0"
                  />
                  <g clip-path="url(#clip0_606_81671)">
                    <path
                      d="M15 24L10 19.7572L11.2498 18.6968L15 21.879L18.7502 18.6968L20 19.7572L15 24ZM15 8.121L11.2498 11.3032L10 10.2427L15 6L20 10.2428L18.7502 11.3025L15 8.121Z"
                      fill="#666B70"
                    />
                  </g>
                  <defs>
                    <clipPath id="clip0_606_81671">
                      <rect
                        width="20"
                        height="20"
                        fill="white"
                        transform="translate(25 5) rotate(90)"
                      />
                    </clipPath>
                  </defs>
                </svg>
              </template>
              <div class="timeline__wrapper">
                <h3 class="showMore">Show 4 more activity</h3>
              </div>
            </v-timeline-item>
          </v-timeline>
        </div>
      </div>
    </v-navigation-drawer>
  </div>
</template>

<script>
export default {
  data() {
    return {
      showDrawer: false,
      elevation: 0,
      width: 512,
      checkedData: true,
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
  methods: {
    closeDrawer() {
      this.showDrawer = false;
    },
    showPanel() {
      this.showDrawer = true;
    },
    handleScroll() {
      const myDiv = this.$refs.myDiv;
      const heightScrolled = myDiv.scrollTop;
      // const initialHeight = myDiv.scrollHeight;
      if (heightScrolled > 0) {
        this.elevation = 2;
      } else {
        this.elevation = 0;
      }
    },
  },
};
</script>

<style lang="scss" scoped>
.text-right {
  width: 100%;
  display: flex;
  justify-content: flex-end;
}
.right-drawer-container {
  padding-bottom: 0 !important;
}
.right-drawer-title {
  margin-bottom: 15px;
  .intro {
    display: flex;
    align-items: center;
    grid-gap: 20px;
    margin-bottom: 14px;
  }
  h1 {
    margin: 0;
  }
  .local__data {
    display: flex;
    justify-content: space-between;
    align-items: center;
    gap: 10px;
    span {
      font-weight: 500;
      font-size: 1.6rem;
      color: var(--label-color);
      &.activityIp {
        padding-left: 10px;
        color: var(--label-third-color);
      }
      &.dActivity {
        font-size: 1.4rem;
        color: var(--primary-color);
        cursor: pointer;
      }
    }
  }
}

.headerTag {
  padding: 47px 47px 0;
}
</style>
