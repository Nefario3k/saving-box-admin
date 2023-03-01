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
        class="mt-2 right-drawer-container"
        @scroll="handleScroll"
      >
        <div>
          <div class="right-drawer-title">
            <h1 class="">Poultry Farm, Wuye Abuja</h1>
            <p>By Thrive Agric Abuja</p>
          </div>
          <div class="admin__content investibox">
            <!-- image  -->
            <div
              style="background-image: url('/images/temporary/investibox.png')"
              class="image__container"
            ></div>

            <!-- name and email  -->
            <div class="pDetails">
              <span class="subHead"
                >Lorem ipsum dolor sit amet consectetur. Orci nisi tortor
                malesuada dictum semper vel risus egestas nec. Sed senectus orci
                nibh sit amet
              </span>
            </div>

            <div class="investiySummary">
              <div class="investiySummary__content">
                <p>₦10,000</p>
                <span>Funding Amount</span>
              </div>
              <div class="investiySummary__content">
                <p>12 Months</p>
                <span>Duration</span>
              </div>
              <div class="investiySummary__content">
                <p>12% per Year</p>
                <span>Expected ROI</span>
              </div>
            </div>

            <div class="investiySummary">
              <div class="investiySummary__content">
                <p>₦10,000</p>
                <span>Per Unit</span>
              </div>
              <div class="investiySummary__content">
                <p>120/500</p>
                <span>Available Units</span>
              </div>
              <div class="investiySummary__content">
                <p>23</p>
                <span>Investors</span>
              </div>
            </div>

            <v-divider></v-divider>
            <div class="pDetails desc">
              <header>Behind Berger Yard, Wuye Abuja, Nigeria</header>
              <span class="subHead">Location Address </span>
            </div>

            <div class="action__area">
              <!-- edit  -->
              <v-btn
                @click="showEditPanel"
                outlined
                class="Btn edit"
                color="var(--primary-color)"
                >Edit</v-btn
              >
              <!-- details  -->
              <v-btn
                to="/investibox/33223"
                class="Btn"
                color="var(--primary-color)"
                >View More Details</v-btn
              >
            </div>
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
    showEditPanel() {
      this.showDrawer = false;
      this.$emit("showEdit");
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
</style>
