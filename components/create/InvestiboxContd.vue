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
            <h1 class="">Create New Investment</h1>
            <p>Create new investment details</p>
          </div>

          <section class="input__area update-form">
            <div class="row">
              <!-- Number of Units  -->
              <div class="col-12">
                <label for="amountPerUnit" class="form-label label-design"
                  >Number of Units</label
                >
                <input
                  type="number"
                  class="form-control input-design"
                  id="amountPerUnit"
                  placeholder="Number of Units"
                />
              </div>
              <!-- Amount per Unit  -->
              <div class="col-12">
                <label for="money" class="form-label label-design"
                  >Amount per Unit</label
                >
                <input
                  type="number"
                  class="form-control input-design"
                  id="money"
                  placeholder="Money"
                />
              </div>
              <!-- Period/Duration  -->
              <div class="col-12">
                <label for="period" class="form-label label-design"
                  >Period/Duration</label
                >
                <input
                  type="text"
                  class="form-control input-design"
                  id="period"
                  placeholder="Period/Duration"
                />
              </div>
              <!-- Interest (ROI)  -->
              <div class="col-12">
                <label for="period" class="form-label label-design"
                  >Interest (ROI)</label
                >
                <input
                  type="number"
                  class="form-control input-design"
                  id="period"
                  placeholder="Interest (ROI)"
                />
              </div>
              <!-- Other Information/Notes  -->
              <div class="col-12">
                <label for="company" class="form-label label-design"
                  >Other Information/Notes</label
                >
                <textarea
                  class="input-design-textarea shortArea"
                  placeholder="Enter Information/Notes here"
                  name=""
                  id=""
                ></textarea>
              </div>

              <div style="margin-top: 31px" class="col-12">
                <button class="btn btn-primary btn-design">Create</button>
              </div>
            </div>
          </section>
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
  },
};
</script>

<style lang="scss" scoped>
.text-right {
  //   position: fixed;
  //   background-color: #fff;
  width: 100%;
  display: flex;
  justify-content: flex-end;
  img {
    // padding-right: 20px;
    // padding-top: 20px;
  }
}
</style>
