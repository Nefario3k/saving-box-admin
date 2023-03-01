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
            <h1 class="">Create Admin</h1>
            <p>Create a new admin</p>
          </div>

          <section class="input__area update-form">
            <div class="row">
              <!-- fname  -->
              <div class="col-12">
                <label for="adminFname" class="form-label label-design"
                  >First Name</label
                >
                <input
                  type="text"
                  class="form-control input-design"
                  id="adminFname"
                  placeholder="First name"
                />
              </div>
              <!-- lname  -->
              <div class="col-12">
                <label for="adminLname" class="form-label label-design"
                  >Last Name</label
                >
                <input
                  type="text"
                  class="form-control input-design"
                  id="adminLname"
                  placeholder="Last name"
                />
              </div>
              <!-- email  -->
              <div class="col-12">
                <label for="adminEmailInput" class="form-label label-design"
                  >Email Address</label
                >
                <input
                  type="email"
                  class="form-control input-design"
                  id="adminEmailInput"
                  placeholder="johndoe@gmail.com"
                />
              </div>
              <!-- number  -->
              <div class="col-12">
                <label for="adminPhoneNumber" class="form-label label-design"
                  >Phone Number</label
                >
                <input
                  type="number"
                  class="form-control input-design"
                  id="adminPhoneNumber"
                  placeholder="234"
                />
              </div>
              <!-- role  -->
              <div class="col-12">
                <label class="form-label label-design">Select Role</label>
                <v-menu :nudge-bottom="3" offset-y max-height="190">
                  <template v-slot:activator="{ on, attrs }">
                    <div v-bind="attrs" v-on="on" class="relative">
                      <input
                        style="cursor: pointer"
                        type="text"
                        disabled
                        value="Compliant Officer"
                        class="form-control input-design"
                        placeholder="234"
                      />
                      <div class="absolute carret">
                        <svg
                          width="14"
                          height="9"
                          viewBox="0 0 14 9"
                          fill="none"
                          xmlns="http://www.w3.org/2000/svg"
                        >
                          <path
                            d="M13 1L7 7L1 1"
                            stroke="#000831"
                            stroke-width="2"
                            stroke-linecap="round"
                          />
                        </svg>
                      </div>
                    </div>
                  </template>
                  <v-list class="dropdown__list">
                    <v-list-item
                      v-for="n in 8"
                      :key="n"
                      class="dropdown__list-item"
                    >
                      <v-list-item-title class="dropdown__list-title"
                        >Compliant Officer</v-list-item-title
                      >
                    </v-list-item>
                  </v-list>
                </v-menu>
              </div>
              <div style="margin-top: 130px" class="col-12">
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
