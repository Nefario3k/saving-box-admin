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
            <h1 class="">John Doe</h1>
            <p>Member</p>
          </div>

          <div class="jolli-card py-4 px-4">
            <div class="key">
              <h3>December Jolly</h3>
              <div class="tag">
                <h3 class="tag">₦100 of ₦100,000</h3>
                <span>Amount Contributed</span>
              </div>
            </div>
            <div class="simple-card-progress">
              <v-progress-linear
                rounded
                value="20"
                height="8px"
                background-color="rgba(227, 227, 227, 1)"
                color="rgba(97, 202, 97, 1)"
              ></v-progress-linear>
              <div class="d-flex justify-content-between">
                <small class="text-left w-50">20% Completed</small>
                <small class="text-right">5 Months Remaining</small>
              </div>
            </div>
          </div>

          <div class="jollyitems-selected">
            <h3>Selected Items</h3>
            <div v-for="n in 7" :key="n + 1299" class="jolly__wrapper">
              <span>Generator X2</span>
              <span class="money">₦98,300</span>
            </div>
            <div class="jolly__wrapper total">
              <span class="total">Total:</span>
              <span class="tMoney">₦130,000</span>
            </div>
          </div>

          <div class="tabsArea">
            <v-tabs
              center-active
              show-arrows
              v-model="jollificationsTab"
              grow
              background-color="transparent"
              color="basil"
              :hide-slider="true"
              class="v-tabs-styles"
            >
              <v-tab :ripple="false"> Pending Invoice</v-tab>

              <v-tab :ripple="false"> Overdue </v-tab>

              <v-tab :ripple="false"> Paid Invoice </v-tab>
            </v-tabs>

            <v-tabs-items
              v-model="jollificationsTab"
              class="tab__items"
              style="padding-left: 10px; padding-right: 10px"
            >
              <v-tab-item v-for="n in 3" :key="n">
                <div class="tab__items">
                  <div class="tab__wrapper">
                    <p>Top up your savings plan</p>
                    <p class="value">N1000</p>
                  </div>
                  <div class="tab__wrapper">
                    <p class="dueDate">Due 9 November 2022, 17:30</p>
                    <p class="value action">Clear Payment</p>
                  </div>
                </div>
                <div v-for="r in 4" :key="r" class="tab__items">
                  <div class="tab__wrapper">
                    <p>Salary Loan Repayment</p>
                    <p class="value">N1000</p>
                  </div>
                  <div class="tab__wrapper">
                    <p class="dueDate">Due 9 November 2022, 17:30</p>
                    <p class="value action">Clear Payment</p>
                  </div>
                </div>
              </v-tab-item>
            </v-tabs-items>
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
