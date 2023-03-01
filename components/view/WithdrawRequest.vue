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
      class="adminPanel"
    >
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
        class="mt-2 right-drawer-container"
        @scroll="handleScroll"
      >
        <div>
          <div class="right-drawer-title">
            <h1 class="">Withdrawal Request Details</h1>
            <p>Withdrawal Information</p>
          </div>

          <div class="keyvalue-container">
            <div class="key-value d-flex justify-space-between">
              <!-- leave the empty tags alone  -->
              <div style="width: 60%">
                <span>Amount:</span>
                <p></p>

                <span>Name:</span>
                <p></p>

                <span>Account Number:</span>
                <p></p>

                <span>Bank Name:</span>
                <p></p>
              </div>
              <div style="width: 40%">
                <span></span>
                <p>₦100,000</p>
                <span></span>
                <p>John Doe</p>
                <span></span>
                <p>30488587573</p>
                <span></span>
                <p>First Bank</p>
              </div>
            </div>
          </div>

          <p class="amount">Amount: <span>₦10,000</span></p>

          <div class="m-0 action__area">
            <v-btn color="var(--primary-color)" class="Btn"
              ><span>Approve</span></v-btn
            >
            <v-btn color="red" outlined class="Btn reject"
              ><span>Reject</span></v-btn
            >
          </div>
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
      jollificationsTab: null,
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
.v-tabs-bar .v-tab:not(.v-tab--active) {
  color: var(--label-second-color) !important;
  font-weight: 600 !important;
  font-size: 14px !important;
  text-transform: capitalize;
  margin: 3px 3px 2px 3px;
  transition: all 0.2s ease-in-out;
}
.v-tabs-bar .v-tab {
  &::before {
    display: none;
  }
}
.amount {
  margin: 36px 0 13px;
  font-weight: 400;
  font-size: 1.6rem;
  color: var(--label-third-color);
  span {
    font-weight: 500;
    padding-left: 7px;
  }
}

.v-tab--active {
  transition: all 0.2s ease-in-out;
  background-color: #ffffff;
  margin: 3px 3px 2px 3px;
  border-radius: 4px;
  font-weight: 600;
  font-size: 14px;
  color: var(--primary-color) !important;
  text-transform: capitalize;
}
</style>
